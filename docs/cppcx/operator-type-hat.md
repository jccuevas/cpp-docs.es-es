---
title: operador Type^
ms.date: 12/30/2016
ms.assetid: b24ffc83-0780-4f9a-8ee0-f5725db339d1
ms.openlocfilehash: fca53abb9dc17588695591d496b7db2a76e319f6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50553665"
---
# <a name="operator-type"></a>operador Type^

Permite la conversión de [Windows::UI::Xaml::Interop::TypeName](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.interop.typename.aspx) en `Platform::Type`.

## <a name="syntax"></a>Sintaxis

```cpp
Operator Type^(Windows::UI::Xaml::Interop::TypeName typeName);
```

### <a name="return-value"></a>Valor devuelto

Devuelve un `Platform::Type` cuando se especifica [Windows::UI::Xaml::Interop::TypeName](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.interop.typename.aspx).

### <a name="remarks"></a>Comentarios

`TypeName` es el struct de Windows en tiempo de ejecución independiente del lenguaje para representar la información de tipo. [Platform::Type](../cppcx/platform-type-class.md) es específico de C++ y no se puede pasar a través de la interfaz binaria de aplicación (ABI). A continuación se muestra un uso de `TypeName`en la función [Navigate](https://msdn.microsoft.com/library/windows/apps/hh702394.aspx) :

```
rootFrame->Navigate(TypeName(MainPage::typeid), e->Arguments);
```

### <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo convertir entre `TypeName` y `Type`.

```

// Convert from Type to TypeName
TypeName tn = TypeName(MainPage::typeid);

// Convert back from TypeName to Type
Type^ tx2 = (Type^)(tn);
```

## <a name="net-framework-equivalent"></a>Equivalente de .NET Framework

Proyecto de programas de .NET framework `TypeName` como <xref:System.Type>

### <a name="requirements"></a>Requisitos

## <a name="see-also"></a>Vea también

[operator Windows::UI::Xaml::Interop::TypeName](../cppcx/operator-windows-ui-xaml-interop-typename.md)<br/>
[Platform::Type (Clase)](../cppcx/platform-type-class.md)