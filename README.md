```bash
function getUrlParam(paramName) {
    const reParam = new RegExp('(?:[\?&]|&)' + paramName + '=([^&]+)', 'i');
    const match = window.location.search.match(reParam);

    return (match && match.length > 1) ? match[1] : null;
}
```
