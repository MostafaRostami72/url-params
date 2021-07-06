```bash
const getUrlParams = (url) => {
    let params = `${url}?`.split('?')[1];
    let query = {};

    if (!isEmpty(params)) {
        params = params.split('&');

        Object.keys(params).map(function (key) {
            const param = params[key].split('=');

            if (param[0].indexOf('[]') !== -1) {
                const itemKey = str_replace('[]', '', param[0]);
                const items = query[itemKey] ?? [];
                items.push(param[1]);

                query[itemKey] = items;
            } else {
                query[param[0]] = param[1];
            }
        });
    }

    return query;
};



function getUrlParam(paramName) {
    const reParam = new RegExp('(?:[\?&]|&)' + paramName + '=([^&]+)', 'i');
    const match = window.location.search.match(reParam);

    return (match && match.length > 1) ? match[1] : null;
}
```
