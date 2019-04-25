---
title: operator Windows::UI::Xaml::Interop::TypeName
ms.date: 12/30/2016
ms.assetid: a65a105e-7e3a-452f-932f-2cdaf00fbba5
ms.openlocfilehash: 5acf17b7c87a71259dba6579d8ee69e0eea86fa5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62161594"
---
# <a name="operator-windowsuixamlinteroptypename"></a>operator Windows::UI::Xaml::Interop::TypeName

Permite la conversión de `Platform::Type` en [Windows::UI::Xaml::Interop::TypeName](/uwp/api/windows.ui.xaml.interop.typename).

## <a name="syntax"></a>Sintaxis

```cpp
Operator TypeName(Platform::Type^ type);
```

### <a name="return-value"></a>Valor devuelto

Devuelve un [Windows::UI::Xaml::Interop::TypeName](/uwp/api/windows.ui.xaml.interop.typename) cuando se especifica `Platform::Type^`.

### <a name="remarks"></a>Comentarios

`TypeName` es el struct de Windows en tiempo de ejecución independiente del lenguaje para representar la información de tipo. [Platform::Type](../cppcx/platform-type-class.md) es específico de C++ y no se puede pasar a través de la interfaz binaria de aplicación (ABI). A continuación se muestra un uso de `TypeName`en la función [Navigate](/uwp/api/windows.ui.xaml.controls.frame.navigate) :

```
rootFrame->Navigate(TypeName(MainPage::typeid), e->Arguments);
```

### <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo convertir entre `TypeName` y `Type`.

```

// Convert from Type to TypeName
Windows::UI::Xaml::Interop::TypeName tn = TypeName(MainPage::typeid);

// Convert back from TypeName to Type
Type^ tx2 = (Type^)(tn);
```

## <a name="net-framework-equivalent"></a>Equivalente de .NET Framework

Proyecto de programas de .NET Framework `TypeName` como [System.Type](assetId:///System.Type?qualifyHint=False&autoUpgrade=True).

### <a name="requirements"></a>Requisitos

## <a name="see-also"></a>Vea también

[operator Windows::UI::Xaml::Interop::TypeName](../cppcx/operator-windows-ui-xaml-interop-typename.md)<br/>
[Platform::Type (Clase)](../cppcx/platform-type-class.md)
