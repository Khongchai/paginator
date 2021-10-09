**Usage**


Along with all paginated result, it also returns the status of isLast and isFirst. For example, you might want to hide your left pagination arrow when the user is seeing the first of all the paginated pages.

```ts

const array = [1, 2, 3, 4, 5, 6];
const limit = 2;
const skip = 0;

const paginator = new Paginator(array, limit, skip);

const stateBeforePagination = paginator.getItemsAtCurrentPage(); // will return {isFirst: true, isLast: false, data: [1, 2]}

if (paginateLeftArrowClicked)
{
  
  paginator.paginateForward();
  const currentState = paginator.getItemsAtCurrentPage();// will return {isFirst: false, isLast: false, data: [3, 4]}
  
  const pagePosition = paginator.getPagePosition(); // will return {page: 2, of: 3}
}

```

React hook example
```ts

export default function usePagination<T>(
  items: T[],
  page: number,
  extraDependencies = [] as any[]
) {
  const paginator = useMemo(() => new Paginator(items, 6, 0), []);

  const res = useMemo(() => {
    paginator.setPage(page);
    paginator.setArray(items);
    const { data: paginatedItems } = paginator.getItemsAtCurrentPage();
    const { page: currentPagePos, of: totalPages } =
      paginator.getPagePosition();

    return { currentPagePos, totalPages, paginatedItems };
  }, [items, page, ...extraDependencies]);

  return { ...res };
}

```

**Parameters**

*Array*

Array to be paginated.

*limit*

The amount of items returned per pagination.

*skip*

Offset pagination beginning position.


[TS Playground](https://www.typescriptlang.org/play?#code/MYGwhgzhAEAKYHMCWA7MAXA9gJ2gbwChppsBTMAE0xRAE9oQkBbJdALmhQFcmAjU7AG4i0AA6JSHbnwHDiEANZJRUnvyEiw2bGFocwKWgG0AunOjBqEdNi7As2ABRade6AeMmANA2atVMtg+isoA-AHqAJT4IsToABZIEAB0jCzo0AC8vunmcYkpLrpZ7tq6edAJSckhoiW10KHQDRwADBVVKeIIpCUAjNAA1NCODQA+Y9CtkeYAvgQiEKToAIJltM7r+obRhMT51UX02UdzC-LL8D2O3ZKcagK7sZUFybclt2ciPegAkuikJgQFboADCXG0pBQ6CupEcT32FisGWsWgy2U6qT8GQAVCNMe8ALTQPozZ6WFDWaAUDBgEqYo41RjAOGo7DoYLoNFDF7VNKsMmIsjoCEoXkpYDxUjABQALQEmAASstRY4aVzBdB5iJuqgMKQAGI4ADuWgo8JiiIJEnpr3ew0x-PQwnJyOptNth3WTKQLMc1p60GJfR8Ad6wZ5juxmuIwtF4uSkulcoVypF2BQatpmu1xF1aABACEwDLTdhzQj9mHPV0bcSo7lzvsKVT1XSMa9GRBmXDq8HQ3a6yTI68nTGSCqMwmkzL5dglZPM22c02frDYJgIKwkNQLXtm26QFCEAka8lGUeUCf4hUWxksFyQLCYNkALIYeKJ0hIECOS-X6AAHoEzHCo4ynfdEVuDgwy8Z5iEwAAzGDMEfZ84MRWYvmIH4VhAEB-kBCA92ecCxQZdZsLEbAkAAN31CwpRlA0kGwawVhQCgABlIHQLMuW2WhK1jRdLURaAkhYtj2ATd5MnkqYMPEpIeOsDg21SY9TwAHhA7ElOILCRFzICcRxWI8V+RCJ3TSlFOaTAmGWRIrwkmBjXnK8fH4YAwC4JYxEQPV0B3MUIHiTAuBACh3BAU1aBgMiHMBKorwswCdRo+iAUY5M5wXWz+LAQTTGEiTrKKzSrx0qYyuIFtMCPZIBHnJwACIrmC0KxE3bdqDchhSCgF4DCmNrx3mIVRMg-Y2wM-ZkkWzEZwUKT2M41S+OXeajMMghtQIO9SlcEojBDaAACYfAAZh8AAWHwAFYfAANjMQ7D2xEoLuEI6GmydoFiO-MMBwEoUFIY04CCgscE2VwfCdYIlFEMkPspFEuSLUhEJwUhOoLbrshBhxkh+QigRBcFIWhWF4UEIDgONH8QBs+M8Ek1i1MqWxSB8FTeI4RCwBAJYfDbDgzp8C6TEm6ACBJnA3hh-UjWwMsK1+t1gAhMhoQAZSx3piZV0nyYBSmwV1qEYQkenAKZlm2YgznpKFkWxbczb3dFvn3QE6AjFu6A7tloG3RJ0KNy3EL+pN5BYewMnLgkaO+szMkGqakBMAQG5Taj3rY5QGYgA)
