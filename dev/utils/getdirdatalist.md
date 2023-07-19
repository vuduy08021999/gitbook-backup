---
description: Hàm gọi lấy data của màn hình list
---

# GetDirDataList

```javascript
export const GetDirDataList = async function(controller, memvars, pageIndex){
    let payload ={
        "folder": "List",
        "controller": controller,
        "memvars": {}
    }
    memvars.pageIndex = pageIndex;

    payload.memvars = memvars;

    let response = await makePostRequest(GET_DIR_DATA_URL, JSON.stringify(payload));
    if(response["status"]==200){
        return response["data"];
    }
}
```
