---
title: healthstack.kit.theme
permalink: /kit/healthstack.kit.theme/index.html

---
//[kit](../../index.html)/[healthstack.kit.theme](index.html)



# Package healthstack.kit.theme



## Types


| Name | Summary |
|---|---|
| [AppColors](-app-colors/index.html) | [androidJvm]<br>class [AppColors](-app-colors/index.html)(primary: Color, primaryVariant: Color, secondary: Color, secondaryVariant: Color, background: Color, surface: Color, error: Color, onPrimary: Color, onSecondary: Color, onBackground: Color, onSurface: Color, onError: Color, isLight: [Boolean](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-boolean/index.html), lightBackground: Color, primaryDark: Color, textPrimary: Color, textPrimaryAccent: Color, textSecondary: Color, textHint: Color, border: Color) |
| [AppTheme](-app-theme/index.html) | [androidJvm]<br>object [AppTheme](-app-theme/index.html) |
| [AppTypography](-app-typography/index.html) | [androidJvm]<br>data class [AppTypography](-app-typography/index.html)(var appTitle: TextStyle = TextStyle(         fontFamily = Inter,         fontWeight = FontWeight.W600,         fontSize = 20.sp     ), val title1: TextStyle = TextStyle(         fontFamily = Inter,         fontWeight = FontWeight.Medium,         fontSize = 40.sp     ), val title2: TextStyle = TextStyle(         fontFamily = Inter,         fontWeight = FontWeight.Medium,         fontSize = 22.sp     ), val title3: TextStyle = TextStyle(         fontFamily = Inter,         fontWeight = FontWeight.W600,         fontSize = 20.sp     ), val subHeader1: TextStyle = TextStyle(         fontFamily = Inter,         fontWeight = FontWeight.W600,         fontSize = 18.sp     ), val subHeader2: TextStyle = TextStyle(         fontFamily = Inter,         fontWeight = FontWeight.W600,         fontSize = 16.sp     ), val topBar: TextStyle = TextStyle(         fontFamily = Inter,         fontWeight = FontWeight.W400,         fontSize = 18.sp     ), val body1: TextStyle = TextStyle(         fontFamily = Inter,         fontWeight = FontWeight.W400,         fontSize = 16.sp     ), val body2: TextStyle = TextStyle(         fontFamily = OpenSans,         fontWeight = FontWeight.W400,         fontSize = 14.sp     ), val body3: TextStyle = TextStyle(         fontFamily = Inter,         fontWeight = FontWeight.W400,         fontSize = 12.sp     ), val body4: TextStyle = TextStyle(         fontFamily = Inter,         fontWeight = FontWeight.W400,         fontSize = 10.sp     )) |


## Functions


| Name | Summary |
|---|---|
| [AppTheme](-app-theme.html) | [androidJvm]<br>@Composable<br>fun [AppTheme](-app-theme.html)(colors: [AppColors](-app-colors/index.html) = AppTheme.colors, typography: [AppTypography](-app-typography/index.html) = AppTheme.typography, shapes: Shapes = MaterialTheme.shapes, content: @Composable() -&gt; [Unit](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-unit/index.html)) |
| [blueColors](blue-colors.html) | [androidJvm]<br>fun [blueColors](blue-colors.html)(primary: Color = Color(0xFF4475E3), primaryVariant: Color = Color(0xFFB3C6F1), secondary: Color = Color(0xFF4475E3), secondaryVariant: Color = Color(0xFFE3EAFB), background: Color = Color(0xFFFFFFFF), surface: Color = Color(0xFFFFFFFF), error: Color = Color(0xFF4475E3), onPrimary: Color = Color(0xFF4475E3), onSecondary: Color = Color(0xFF4475E3), onBackground: Color = Color(0xFFFFFFFF), onSurface: Color = Color(0xFF2D2D2D), onError: Color = Color(0xFF4475E3), isLight: [Boolean](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-boolean/index.html) = true, lightBackground: Color = Color(0xFFF7F8FA), primaryDark: Color = Color(0xFF68A8FF), textPrimary: Color = Color(0xFF474747), textPrimaryAccent: Color = Color(0xFF4475E3), textSecondary: Color = Color(0xFFFFFFFF), textHint: Color = Color(0xFF808080), border: Color = Color(0xFFB3C6F1)): [AppColors](-app-colors/index.html) |
| [darkBlueColors](dark-blue-colors.html) | [androidJvm]<br>fun [darkBlueColors](dark-blue-colors.html)(primary: Color = Color(0xFF68A8FF), primaryVariant: Color = Color(0xFF68A8FF), secondary: Color = Color(0xFF68A8FF), secondaryVariant: Color = Color(0xFF68A8FF), background: Color = Color(0xFF1E1E1E), surface: Color = Color(0xFF232527), error: Color = Color(0xFF4475E3), onPrimary: Color = Color(0xFF68A8FF), onSecondary: Color = Color(0xFF4475E3), onBackground: Color = Color(0xFFFFFFFF), onSurface: Color = Color(0xFFEEEEEE), onError: Color = Color(0xFF4475E3), isLight: [Boolean](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-boolean/index.html) = false, lightBackground: Color = Color(0xFF232527), primaryDark: Color = Color(0xFF68A8FF), textPrimary: Color = Color(0xFFFFFFFF), textPrimaryAccent: Color = Color(0xFF4475E3), textSecondary: Color = Color(0xFF232527), textHint: Color = Color(0xFF979797), border: Color = Color(0xFF4475E3)): [AppColors](-app-colors/index.html) |
| [darkColors](dark-colors.html) | [androidJvm]<br>fun [darkColors](dark-colors.html)(primary: Color = Color(0xFFFF9E00), primaryVariant: Color = Color(0xFFFF9E00), secondary: Color = Color(0xFFFF9E00), secondaryVariant: Color = Color(0xFFFF9E00), background: Color = Color(0xFF141414), surface: Color = Color(0xFF2E2E2E), error: Color = Color(0xFFFF9E00), onPrimary: Color = Color(0xFFFF9E00), onSecondary: Color = Color(0xFFFF9E00), onBackground: Color = Color(0xFFFFFFFF), onSurface: Color = Color(0xFFFF9E00), onError: Color = Color(0xFFFF9E00), isLight: [Boolean](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-boolean/index.html) = true, lightBackground: Color = Color(0xFF5A5A5A), primaryDark: Color = Color(0xFFFF9E00), textPrimary: Color = Color(0xFFFFFFFF), textPrimaryAccent: Color = Color(0xFFFF9E00), textSecondary: Color = Color(0xFFFFFFFF), textHint: Color = Color(0xFFADA597), border: Color = Color(0xFFFFFFFF)): [AppColors](-app-colors/index.html) |
| [lightColors](light-colors.html) | [androidJvm]<br>fun [lightColors](light-colors.html)(primary: Color = Color(0xFFFF9E00), primaryVariant: Color = Color(0xFFFF9E00), secondary: Color = Color(0xFFFF9E00), secondaryVariant: Color = Color(0xFFFF9E00), background: Color = Color(0xFFFFFFFF), surface: Color = Color(0xFFFFFFFF), error: Color = Color(0xFFFF9E00), onPrimary: Color = Color(0xFFFF9E00), onSecondary: Color = Color(0xFFFF9E00), onBackground: Color = Color(0xFFFFFFFF), onSurface: Color = Color(0xFFFF9E00), onError: Color = Color(0xFFFF9E00), isLight: [Boolean](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-boolean/index.html) = true, lightBackground: Color = Color(0xFFFFFFFF), primaryDark: Color = Color(0xFF443F36), textPrimary: Color = Color(0xFF130C00), textPrimaryAccent: Color = Color(0xFFFF9E00), textSecondary: Color = Color(0xFF443F36), textHint: Color = Color(0xFF746B5C), border: Color = Color(0xFF343A40)): [AppColors](-app-colors/index.html) |


## Properties


| Name | Summary |
|---|---|
| [Inter](-inter.html) | [androidJvm]<br>val [Inter](-inter.html): FontFamily |
| [OpenSans](-open-sans.html) | [androidJvm]<br>val [OpenSans](-open-sans.html): FontFamily |

