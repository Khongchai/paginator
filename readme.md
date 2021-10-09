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

export default function usePagination<T>(items: T[], page: number) {
  const paginator = useMemo(() => new Paginator(items, 7, 0), []);

  const res = useMemo(() => {
    paginator.setPage(page);
    const { data: paginatedItems } = paginator.getItemsAtCurrentPage();
    const { page: currentPagePos, of: totalPages } =
      paginator.getPagePosition();

    return { currentPagePos, totalPages, paginatedItems };
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


[TS Playground](https://www.typescriptlang.org/play?#code/MYGwhgzhAEAKYHMCWA7MAXA9gJ2gbwChppsBTMAE0xRAE9oQkBbJdALmhQFcmAjU7AG4i0AA6JSHbnwHDiEANZJRUnvyEiw2bGFocwKWgG0AunOjBqEdNi7As2ABRade6AeMmANA2atVMtg+isoA-AHqAJT4IsToABZIEAB0jCzo0AC8vunmcYkpLrpZ7tq6edAJSckhoiW10KHQDRwADBVVKeIIpCUAjNAA1NCODQA+Y9CtkeYAvgQiEKToAIJltM7r+obRhMT51UX02UdzC-LL8D2O3ZKcagK7sZUFybclt2ciPegAkuikJgQFboADCXG0pBQ6CupEcT32FisGQoGDAJU6ySONUYwDhmPeAFpoH0fASJNBiQNhpi0qwZs8yOgISgXtVgPFSMAFAAtASYABKyxZjlR6DADOI8xE3VQGFIADEcAB3LQUeExRHknoY17vGmvOnoYTPSwoazQMXo7KY7EQXH4vUUqlkp06qlDNkpI2S-ZMlle5Icrm8-lC5nYFCitG+6XEWVoAEAITA3NV2HVCP22t6NrdvWJtL8xvO+zNFqtusO6xxSDxjhzlJJruqRJJnqL6V9xH9kcDwe5fOwguFkej4tjpZ+sNgmAgrCQ1A1ezLyIYUIQCSrhRrIA3CQq5YyWHFIFhMGyAFkMPEg6QkCBHHuUJv4tAAPSBn0VXusleI24OBzLxnmITAADMgMwU9zxAxFZi+YgfhWEAQH+QEIGXRlR1ZW11kQsRsCQAA3eULE5bkFSQbBrBWFAKAAGUgdBxzAbZaCzHscM1RFoCSKiaPYQN3kyUSpjg3ikiY6wOCtVJ9zfAAeL9iwkqUCPfAAqTTYk06BfnAkgcJgVpgkwJhlkSF8+JgZVhxfHx+GAMAuCWMREDldBF1ZCB4kwLgQAodwQFVWgYF-ZpMEBKoX1098ZSI0iAXIkMhxHCMoytdjTE4vjDNY+SXy3ZTph4xFy0wPdkgEYcnAAIiuTzvLEOcF2oGz1ygF4DCmOru2geZEQi-99itNT9mSSbMQHBQBNo+jpJYq1InGhCRHmaUCCPUpXBKIxSWgAAmHwAGYfAAFh8ABWHwADYzC2tcjRKQ7hG2hpsnaBZtoTDAcBKFBSGVOAPMTHBNlcHwjWCJRRAZR7zQyax5STUhwJwUhGsTZrsl+hxkh+dCgRBcFIWhWF4UED9P2VB8QCMjL8H46iZMqWxSB8KTmI4cCwBAJYfCy6B9p8Q6TEG6ACDxnA3lB+UlWwdNMzetdgAhMhoQAZXFZLcbl-HCYBYmwXVqEYQkSn3xpumGYDPBmcEnm+YFmzFqd-mOctNEOCMM7oHO8XvrXPHvNnecvPavXkDB7ACcuCQw7aqMGQqqqQEwBAbn10PWojlAZiAA)
