---
description: Dùng để alert thông báo một nội dung nào đó lên màn hình điện thoại
---

# AAlert

## Source code

{% code title="App.js" %}
```javascript
AAlert = handlePress;
```
{% endcode %}

{% code title="App.js" %}
```javascript
const handlePress = ({title, message, icon, callback}) => {
    setAlertData({
      title: title || '',
      visible: true,
      message: message || '',
      icon: icon || '',
      callback: callback
        ? callback
        : () => {
            return;
          },
    });
  };
```
{% endcode %}

{% code title="App.js" %}
```javascript
import {AAlertComponent, APopupNotificationComponent, ALoadingComponent, ZC_BottomButton} from './src/core/utils/screenServices';
<AAlertComponent data={alertData} onDismiss={handleDismiss} />
```
{% endcode %}

{% code title="./src/core/utils/screenService.jss" %}
```javascript
export const AAlertComponent = ({ data, onDismiss }) => {
  return (
    <Modal visible={data.visible} transparent animationType='slide'>
      <View style={{ flex: 1, backgroundColor: 'rgba(0, 0, 0, 0)', justifyContent: 'center', alignItems: 'center' }}>
        <View style={{ backgroundColor: 'white', padding: 20, borderRadius: 10, width:"70%" }}>
          <View style={{...AStyle.Group}}>
            {
            data.icon?
              <Image
                source={{ uri: data.icon}}
                style={{ width: 24, height: 24 }}
              />:null
            }
            <View style={{height:24, justifyContent: 'center', alignItems: 'center', marginLeft:8}}>
              <Text style={{ fontSize: 18, color:ATheme.textColorPrimary }}>{data.title}</Text>
            </View>
            
            <View style={{width:"100%", marginTop:20}}>
              <Text style={{ color:ATheme.textColorPrimary }}>{data.title}</Text>
            </View>
          
          </View>
          <TouchableOpacity onPress={()=>{onDismiss(); data.callback()}} style={{ marginTop: 20, backgroundColor: '#2196f3', padding: 10, borderRadius: 5 }}>
            <Text style={{ color: 'white', fontSize: 16, textAlign: 'center', textAlignVertical: 'center' }}>OK</Text>
          </TouchableOpacity>
        </View>
      </View>
    </Modal>
  );
};
```
{% endcode %}

## Giải thích

Hàm AAlert được gọi truyền vào 4 tham số {title, message, icon, callback}\
title: là tiêu đề của thông báo (string)\
message: Là nội dung tin nhắn (string)\
icon: là link ảnh (https) hoặc dạng base64\
callback: là hàm muốn xử lý khi người dùng ấn nút ok

## Ví dụ&#x20;

```javascript
AAlert({
  title:"title alert",
  message:"Message xin chào alert", 
  icon: "https://www.iconhot.com/icon/png/quiet/256/information.png",
  callback:()=>{
    console.log("Người dùng vừa ấn đóng alert");
  }
});
```

Vì hàm này có thể gọi từ bất kỳ đâu, nên khi gọi màn hình sẽ xuất hiện thông báo, khi bấm vào ok thì thông báo bị ẩn đi, đồng thời nó gọi hàm callback

<figure><img src="../../.gitbook/assets/image (6).png" alt=""><figcaption></figcaption></figure>

Hàm này được sử dụng trong tình huống nhận notification dạng alert-active, tức là sau khi thông báo một cái gì đó nó sẽ thực hiện một hành động, hành động ở đây định nghĩa bằng callback
