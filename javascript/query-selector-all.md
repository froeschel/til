# Document.querySelectorAll()

The method returns a node list of elements that match a group of specified selectors. Syntax:

```
document.querySelectorAll('input:not([required]), select:not([required]), textarea:not([required])').forEach((el) => {
  el.disabled = true;
});

```
