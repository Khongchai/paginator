**Usage**


Along with all results, it also returns the status of isLast and isFirst. For example, you might want to hide your left pagination arrow when the user is seeing the first of all the paginated pages.

```ts

const array = [1, 2, 3, 4, 5, 6];
const limit = 2;
const skip = 0;

const paginator = new Paginator(array, limit, skip);

if (paginateLeftArrowClicked)
{
  const stateBeforePagination = paginator.getItemsAtCurrent(); // will return {isFirst: true, isLast: false, data: [1, 2]}
  
  paginator.paginateForward();
  const currentState = paginator.getItemsAtCurrent();// will return {isFirst: false, isLast: false, data: [3, 4]}
  
  const pagePosition = paginator.getPagePosition(); // will return {page: 2, of: 3}
}

```

**Parameters**

*Array*

Array to be paginated.

*limit*

The amount of items returned per pagination.

*skip*

Offset pagination beginning position.

