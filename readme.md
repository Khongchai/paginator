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


[TS Playground](https://www.typescriptlang.org/play?#code/MYGwhgzhAEAKYHMCWA7MAXA9gJ2gbwChppsBTMAE0xRAE9oQkBbJdALmhQFcmAjU7AG4i0YF2xkU7Tj35CREANZIADh258Bw4mAlhaHMCloBtALrbR1COmxdgWbAApd2fYePmANA2at1sgI+SqoA-AGa2ACU+CLE6AAWSBAAdIws6NAAvL4ZlvFJqa762dDFtPnQickpISqlddCh0I0cAAyV1aliEqRSpW3QANRVhbXKKpYAvgQiCKToAJLopEwQAILoAMLikuhOMYTExMDWmRQYYKVdKeW1jMCkTjc9ez4vu32ZIzfprFGVMjocQoUY1YAJUjARQALQEmAASgsQU4LugwACRDMRCpEKgMKQAGI4ADuugoB1ixzB3U+-RyH16-R+Yz+6GEcSsKBs0DRVwZYzuEAeT0ZbxpKVeX2GErZmOpQJBEohUNh8KRwOwKFRl3l0GxxFxyDQKwAQmBoWTsBTDpyxdKBeC6ZkALSyvzs2bU07c86Xa6CvS0e5IR7PMZSqTvCPOmW-D164iKrXKyHQuHYRHIrU69F6g3QeboeDzWCYCCsJDUSlHY4+nkgPoIRIBmp3RsoZsJSr1zJYdEgEukGA5ACyGASktISBATg7XegAHp3RlE1yeZHi4hSKVx4kpzOnOGnUzvtAAIwxZfx1eA7Og2vUo2kDibofZLI5QbNc-QV-OocvE5YhMAAMw4fswEHbcICA6kpmmL1CwWdYQBAZZVggGtOWTUEbnKRCcWwJAADcCVENNFEJJBsBsdYUAoAAZSB9j5DxaFtBV7ypaloGSajaOke16U-aA2jg3jkmYmwOD5NImxbAAeFdWAk4gEKxJDFwAKm0uJtOgRZQJIe8YHElpMCYBYkk7PiYBJTNOx8fhgDALgIB3I18XQKtQQgBJMC4EAKDKEAyVoGBcIs1Zqk7fTFyI0jyJVdN1XvXMwHY8xOOOJBjIy+TOyUsScu9axMEbFIBEzZwACIS283zoBUctK2oOyGGHGBEiMMTarXGYuM1B9gN5S41OOFIppeSiBLohjpNY3UJo09SCGxXsyiDUoTHPHwACYfAAZh8AAWHwAFYfAANgsAhNrZUp9uETbGi-DlNq8k0cFKFBSBJOA8W+5xyh8NlggmTF7rOFp0TNUhQJwUgGpNJqci+jAcBSIsMLWTYdlPA5BCXZcSRnEATOG-B+JomSqjsUgfCkliOFAqCPJ8NjoF2g6zEG6ACAxxwUiFolSXJInod9URnQAZThnd0aBzHsGxhZcY2bZnSJxdSfJymlTwGnBNZ9nGbsxbTZADmxvRDgTBO6BTr52ZPuVnzqDLCsPdBJXjRVtWt1LVqfcl+sKtINJMAQJwhd8r22pQAEgA)
