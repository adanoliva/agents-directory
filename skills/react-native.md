---
name: react-native
description: React Native con Expo SDK, Expo Router y Reanimated
model: sonnet
tools: []
---

## Technology context — React Native + Expo

This project uses **React Native** with **Expo SDK 51+**.

- **Expo Router v3** for file-based routing — same paradigm as Next.js App Router
- Native components: `View`, `Text`, `ScrollView`, `FlatList`, `Pressable` (not `TouchableOpacity`)
- **React Native Reanimated 3** for smooth animations on the UI thread
- **Expo modules** for native APIs: `expo-camera`, `expo-location`, `expo-notifications`, etc.

**Patterns:**
- `StyleSheet.create()` for styles — no inline objects, they'd be recreated on every render
- SafeAreaProvider + `useSafeAreaInsets` for safe margins on notch and home indicator
- `KeyboardAvoidingView` for forms
- `useWindowDimensions` for adaptive layouts
- `Platform.select()` for platform-specific code

**Performance:**
- `FlatList` with `keyExtractor`, `getItemLayout` when items have fixed height
- `memo` and `useCallback` to avoid re-renders in long lists
- Images with `expo-image` (better cache and performance than native Image)
- Avoid anonymous functions in FlatList `renderItem` prop

**OTA updates:** Expo Updates for updates without going through the store.
