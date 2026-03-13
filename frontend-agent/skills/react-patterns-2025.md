# Skill: React Patterns 2025/2026
**Version:** 1.0 | **Date:** 2026-03-13 | **Agent:** Nova 🎨

## Custom Hooks Pattern
```javascript
// hooks/usePayment.js — extract complex logic
export function usePayment() {
  const [loading, setLoading] = useState(false);
  const [error, setError] = useState(null);
  const checkout = async (planId) => {
    setLoading(true);
    try {
      const session = await createCheckoutSession(planId);
      window.location = session.url;
    } catch (err) {
      setError(err.message);
    } finally {
      setLoading(false);
    }
  };
  return { checkout, loading, error };
}
```

## Error Boundary
```javascript
// Always wrap page-level components
<ErrorBoundary fallback={<ErrorPage />}>
  <PaymentPage />
</ErrorBoundary>
```

## Performance: useMemo/useCallback
```javascript
// Only memoize expensive computations or stable callbacks
const filteredOccupations = useMemo(
  () => occupations.filter(o => o.visaType === selectedVisa),
  [occupations, selectedVisa]
);
```

## Common mistakes to avoid
- ❌ useEffect với missing deps — causes stale closures
- ❌ State mutations (always spread: `setState({...prev, key: val})`)
- ❌ Fetch in render — always in useEffect or event handler
- ❌ Key prop as index when list can reorder

## Performance: 2026 Updates (Vercel react-best-practices + LogRocket)

### React Compiler (React 19+)
- React Compiler auto-memoizes — **reduce manual useMemo/useCallback** in new code
- Use React DevTools Profiler + performance tracks to find bottlenecks before guessing

### LCP optimization (key metric)
- LCP was cut from 28s → ~1s with: profiling, smart bundling, SSR, lazy loading
- `React.lazy()` + `Suspense` for route-level code splitting (mandatory for large apps)
- Use `webpack-bundle-analyzer` or Vite's rollup plugin to spot large deps

### Vercel 40+ rules (Feb 2026 release) — top priorities
1. **Avoid client-side data fetching for SEO-critical content** — use SSR/RSC instead
2. **Prefer Server Components** (Next.js) for static/non-interactive sections
3. **Image optimization** — always use `next/image` or equivalent; never raw `<img>` for above-fold
4. **Minimize JS bundle** — each unused export costs paint time

### Core Web Vitals targets (2026)
| Metric | Target |
|--------|--------|
| LCP | < 2.5s |
| INP (replaced FID) | < 200ms |
| CLS | < 0.1 |

## Changelog
- v1.0: Initial bootstrap
- v1.1 (2026-03-13): Added React 19 Compiler notes, Vercel best-practices rules, LCP optimization, Core Web Vitals 2026 targets
