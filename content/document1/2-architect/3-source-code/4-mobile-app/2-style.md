---
sidebar_position: 2
---
# ✨ Style

Style chung cho toàn bộ ứng dụng

```
styles
├── GlobalStyles.ts
└── GlobalThemes.ts
```

## GlobalStyles.ts

Các style được setup sẵn sử dụng cho toàn bộ dự án.
``` typescript
import { StyleSheet } from 'react-native';
import { GlobalTheme } from './GlobalThemes';
export const GlobalStyles = StyleSheet.create({
  body: {
    flex: 1,
    position: 'relative',
  },
  backGroundColorWhite: {
    backgroundColor: '#fff',
  },
  backGroundColorPrimary: {
    backgroundColor: GlobalTheme.colors.primary
  },
  backGroundColorSecondary: {
    backgroundColor: GlobalTheme.colors.secondary
  }
  ,
  displayFlex: {
    display: 'flex',
  },
  flexDirectionRow: {
    flexDirection: 'row'
  },
  flexDirectionColumn: {
    flexDirection: 'column'
  },
  flexWrap: {
    flexWrap: 'wrap'
  },
  justifyContentCenter: {
    justifyContent: 'center',
  },
  justifyContentEnd: {
    justifyContent: 'flex-end',
  },
  alignItemsEnd: {
    alignItems: 'flex-end',
  },
  alignItemsCenter: {
    alignItems: 'center',
  },
  justifyContentSpaceBetween: {
    justifyContent: 'space-between'
  },
  spacer: {
    flex: 1
  },
  borderBottom:{
    borderBottomWidth:0.5,
    borderBottomColor:"#303030"
  },
  shadow: {
    shadowColor: "#000",
    shadowOffset: {
      width: 0,
      height: 2,
    },
    shadowOpacity: 0.23,
    shadowRadius: 2.62,

    elevation: 4,
  }
});

```

## GlobalThemes.ts

Setup các màu sắc chủ đạo, nhất quán cho toàn bộ ứng dụng.

:::tip
Thay đổi colors.primary thay đổi màu chính của ứng dụng. Thay đổi colors.secondary thay đổi màu phụ của ứng dụng.
:::

``` typescript
import {
  MD3LightTheme as DefaultTheme,
  Provider as PaperProvider,
} from 'react-native-paper';

export const GlobalTheme = {
  ...DefaultTheme,
  colors: {
    ...DefaultTheme.colors,
    primary: 'rgba(3,96,135,1)',
    secondary: '#ffb380',
    inversePrimary: '#59c1cc',
    inverseSurface: 'rgba(255,255,255,1)',
    inverseOnSurface: 'rgba(0,0,0,1)',
    elevation: {
      level0: 'transparent',
      // Note: Color values with transparency cause RN to transfer shadows to children nodes
      // instead of View component in Surface. Providing solid background fixes the issue.
      // Opaque color values generated with `palette.primary99` used as background
      level1: 'rgba(255,255,255,1)', // palette.primary40, alpha 0.05
      level2: 'rgba(255,255,255,1)', // palette.primary40, alpha 0.08
      level3: 'rgba(255,255,255,1)', // palette.primary40, alpha 0.11
      level4: 'rgba(255,255,255,1)', // palette.primary40, alpha 0.12
      level5: 'rgba(255,255,255,1)', // palette.primary40, alpha 0.14
    },
  },
};


```
