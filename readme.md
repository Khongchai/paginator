**Usage**


Along with all paginated result, it also returns the status of isLast and isFirst. For example, you might want to hide your left pagination arrow when the user is seeing the first of all the paginated pages.

```ts

const array = [1, 2, 3, 4, 5, 6];
const limit = 2;
const skip = 0;

const paginator = new Paginator(array, limit, skip);

const stateBeforePagination = paginator.getItemsAtCurrent(); // will return {isFirst: true, isLast: false, data: [1, 2]}

if (paginateLeftArrowClicked)
{
  
  paginator.paginateForward();
  const currentState = paginator.getItemsAtCurrent();// will return {isFirst: false, isLast: false, data: [3, 4]}
  
  const pagePosition = paginator.getPagePosition(); // will return {page: 2, of: 3}
}

```

React hook example
```ts

export default function usePagination(items: any[], page: number) {
  const paginator = useMemo(() => new Paginator(items, 7, 0), []);

  const res = useMemo(() => {
    paginator.setPage(page);
    const { data: paginateditems } = paginator.getItemsAtCurrentPage();
    const { page: currentPagePos, of: totalPages } =
      paginator.getPagePosition();

    return { currentPagePos, totalPages, paginateditems };
  }, [items, page]);

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


[TS Playground](https://www.typescriptlang.org/play?ssl=88&ssc=33&pln=1&pc=1#code/MYGwhgzhAEAKYHMCWA7MAXA9gJ2gbwChppsBTMAE0xRAE9oQkBbJdALmhQFcmAjU7AG4i0AA6JSHbnwHDiEANZJRUnvyEiw2bGFocwKWgG0AunOjBqEdNi7As2ABRade6AeMmANA2atVMtg+isoA-AHqAJT4IsToABZIEAB0jCzo0AC8vunmcYkpLrpZ7tq6edAJSckhoiW10KHQDRwADBVVKeIIpCUAjNAA1NCODQA+Y9CtkeYAvgQiEKToAIJltM7r+obRhMT51UX02UdzC-LL8D2O3ZKcagK7sZUFybclt2ciPegAkuikJgQFboADCXG0pBQ6CupEcT32FisGQoGDAJU6ySONUYwDhmPeAFpoH0fASJNBiQNhpi0qwZs8yOgISgXtVgPFSMAFAAtASYABKyxZjlR6DADOI8xE3VQGFIADEcAB3LQUeExRHknoY17vGmvOnoYTPSwoazQMXo7KY7EQXH4vUUqlkp06qlDNkpI2S-ZMlle5Icrm8-lC5nYFCitG+6XEWVoAEAITA3NV2HVCP22t6NrdvWJtL8xvO+zNFqtusO6xxSDxjhzlJJruqRJJnqL6V9xH9kcDwe5fOwguFkej4tjpZ+sNgmAgrCQ1A1ezLyIYUIQCSrhRrIA3CQq5YyWHFIFhMGyAFkMPEg6QkCBHHuUJv4tAAPSBn2HtfACFkaFYRKa8EjvB8G3zD8v2LbsSFHVkV0RW4OD-SFAIpTJMKmRp2xQ-8oRhCQvGeYhMAAMw4E8wDPCQIGIxFZi+YgfhWEAQH+QEIGXRl4MDU4RDjMRsCQAA3eULE5bkFSQbBrBWFAKAAGUgdBxzAbZaCzHteMQ-Ykmk2T2EDd5MOyVp6MRaAkmU6wOCtVJ9zfAAeaD0gsqUmI-AAqLzYi86BfjIuCI3NKZgkwJhlkSF8rJgZVhxfHx+GAMAuCWMREDldBF1ZCB4kwLgQAodwQFVWgYF7XLMEBKoXz898ZWEsSAQkkMhxHEK1I00wtKsoK1Icl8txc6ZNUs8tMD3ZIBGHJwACIriynKxDnBdqFi9coBeAwpjm2D5kRSqxsRK13P2ZILsxAcFAMuSFJs1SrUiM7GIEghpQII9SlcEojFJaAACYfAAZh8AAWHwAFYfAANjMT61yNEoAeEL6GjMk0voTDAcBKFBSGVOBMsTHBNlcHwjWCJRRAZBHzQyax5STUgyJwUhFsTZbsmxhxkh+DigRBcE0MI64Zg-T9lQfEBgoDPB9Jk2zKlsUgfGslSODI6ilh8K0OD+nwAZMA7oAIHmcDeYn5SVbB00zVHf3w6EAGVxRa7mrd5-mAUFsEndFuEZnfSXpdlvt5YgW6jK1kAddih7Ne11XLTRfXQegMHjYWLHPZy2d52y9aPeQEnsD5y4JHztaowZCappATAEBuXPqCrwuUBmIA)
