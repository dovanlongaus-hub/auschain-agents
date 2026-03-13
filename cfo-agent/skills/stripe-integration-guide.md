# Skill: Stripe Integration Guide
**Version:** 1.0 | **Date:** 2026-03-13 | **Agent:** Rex 💰

## Setup (Backend — Node.js)
```javascript
import Stripe from 'stripe';
const stripe = new Stripe(process.env.STRIPE_SECRET_KEY);

// Create checkout session
app.post('/api/create-checkout', authenticate, async (req, res) => {
  const { planId } = req.body;
  const prices = { basic: 'price_xxx', pro: 'price_yyy', expert: 'price_zzz' };
  
  const session = await stripe.checkout.sessions.create({
    mode: 'subscription',
    payment_method_types: ['card'],
    line_items: [{ price: prices[planId], quantity: 1 }],
    success_url: `${process.env.APP_URL}/success?session_id={CHECKOUT_SESSION_ID}`,
    cancel_url: `${process.env.APP_URL}/pricing`,
    customer_email: req.user.email,
    metadata: { userId: req.user.id, planId },
  });
  res.json({ url: session.url });
});
```

## Webhook (verify + handle events)
```javascript
app.post('/api/stripe-webhook', express.raw({ type: 'application/json' }), (req, res) => {
  const sig = req.headers['stripe-signature'];
  let event;
  try {
    event = stripe.webhooks.constructEvent(req.body, sig, process.env.STRIPE_WEBHOOK_SECRET);
  } catch (err) {
    return res.status(400).send(`Webhook Error: ${err.message}`);
  }
  
  switch (event.type) {
    case 'checkout.session.completed':
      await activateSubscription(event.data.object);
      break;
    case 'customer.subscription.deleted':
      await deactivateSubscription(event.data.object);
      break;
  }
  res.json({ received: true });
});
```

## Frontend — redirect to checkout
```javascript
const { checkout, loading } = usePayment();
<button onClick={() => checkout('pro')} disabled={loading}>
  {loading ? 'Loading...' : 'Upgrade to Pro $25/mo'}
</button>
```

## No-code option: Stripe Payment Link
- Dashboard → Products → Payment Links
- Set price, billing interval, redirect URL
- Share link directly — zero code needed
- Best for: suong-chat quick launch

## Pricing for visa-path-aus (AUD)
```
basic:  $12 AUD/month (price_basic_aud)
pro:    $25 AUD/month (price_pro_aud)
expert: $45 AUD/month (price_expert_aud)
```

## Common mistakes
- ❌ Using publishable key on backend (use secret key server-side only)
- ❌ Not verifying webhook signature — security vulnerability
- ❌ Trusting frontend success redirect without webhook confirmation

## Changelog
- v1.0: Initial bootstrap
