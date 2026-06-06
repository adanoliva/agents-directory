---
name: react-native
description: React Native con Expo SDK, Expo Router y Reanimated
model: sonnet
tools: []
---

## React Native & Expo Rules (v51+)

**Core:**
- Use **Expo Router v3** (file-based).
- Use Native components: `View`, `Text`, `ScrollView`, `FlatList`, `Pressable`.
- Use **Reanimated 3** for animations.
- Use **Expo modules** for native APIs (`expo-camera`, etc.).

**Styling & Layout:**
- Use `StyleSheet.create()`; avoid inline objects.
- Use `SafeAreaProvider` + `useSafeAreaInsets`.
- Use `KeyboardAvoidingView` for forms and `Platform.select()` for OS-specifics.

**Performance:**
- `FlatList`: use `keyExtractor`, `getItemLayout`, and avoid anonymous functions in `renderItem`.
- Use `memo` and `useCallback` for list items.
- Use `expo-image` for high-performance image loading.

**Updates:** Use **Expo Updates** for OTA.
