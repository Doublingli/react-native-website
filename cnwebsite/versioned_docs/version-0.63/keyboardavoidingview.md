---
id: version-0.63-keyboardavoidingview
title: KeyboardAvoidingView
original_id: keyboardavoidingview
---

##### 本文档贡献者：[sunnylqm](https://github.com/search?q=sunnylqm&type=Users)(100.00%)

本组件用于解决一个常见的尴尬问题：手机上弹出的键盘常常会挡住当前的视图。本组件可以自动根据键盘的高度，调整自身的 height 或底部的 padding，以避免被遮挡。

## 示例

```SnackPlayer name=KeyboardAvoidingView&supportedPlatforms=android,ios
import React from 'react';
import { View, KeyboardAvoidingView, TextInput, StyleSheet, Text, Platform, TouchableWithoutFeedback, Button, Keyboard  } from 'react-native';

const KeyboardAvoidingComponent = () => {
  return (
    <KeyboardAvoidingView
      behavior={Platform.OS == "ios" ? "padding" : "height"}
      style={styles.container}
    >
      <TouchableWithoutFeedback onPress={Keyboard.dismiss}>
        <View style={styles.inner}>
          <Text style={styles.header}>Header</Text>
          <TextInput placeholder="Username" style={styles.textInput} />
          <View style={styles.btnContainer}>
            <Button title="Submit" onPress={() => null} />
          </View>
        </View>
      </TouchableWithoutFeedback>
    </KeyboardAvoidingView>
  );
};

const styles = StyleSheet.create({
  container: {
    flex: 1
  },
  inner: {
    padding: 24,
    flex: 1,
    justifyContent: "space-around"
  },
  header: {
    fontSize: 36,
    marginBottom: 48
  },
  textInput: {
    height: 40,
    borderColor: "#000000",
    borderBottomWidth: 1,
    marginBottom: 36
  },
  btnContainer: {
    backgroundColor: "white",
    marginTop: 12
  }
});

export default KeyboardAvoidingComponent;
```

---

# 文档

## Props

### `keyboardVerticalOffset`

有时候应用离屏幕顶部还有一些距离（比如状态栏等等），利用此属性来补偿修正这段距离。

| 类型   | 必填 |
| ------ | ---- |
| number | 否   |

---

### `behavior`

Specify how to react to the presence of the keyboard.

> Android 和 iOS 在此属性上表现并不一致。但我们建议在两个平台上都明确设置此属性。

| 类型                                  | 必填 |
| ------------------------------------- | ---- |
| enum('height', 'position', 'padding') | 否   |

---

### `contentContainerStyle`

如果设定 behavior 值为'position'，则会生成一个 View 作为内容容器。此属性用于指定此内容容器的样式。

| 类型       | 必填 |
| ---------- | ---- |
| View.style | 否   |

### `enabled`

是否启用 KeyboardAvoidingView。默认为 true。

| 类型    | 必填 |
| ------- | ---- |
| boolean | 否   |
