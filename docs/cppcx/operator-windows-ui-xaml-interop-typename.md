---
title: operador Windows::UI::Xaml::Interop::TypeName | Microsoft Docs
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: language-reference
ms.assetid: a65a105e-7e3a-452f-932f-2cdaf00fbba5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0cf5041e6e3faa8c495d52c31d86ff25c903a174
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "42600725"
---
# <a name="operator-windowsuixamlinteroptypename"></a>operator Windows::UI::Xaml::Interop::TypeName
Permite la conversión de `Platform::Type` en [Windows::UI::Xaml::Interop::TypeName](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.interop.typename.aspx).  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
Operator TypeName(Platform::Type^ type)  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve un [Windows::UI::Xaml::Interop::TypeName](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.interop.typename.aspx) cuando se especifica `Platform::Type^`.  
  
### <a name="remarks"></a>Comentarios  
 `TypeName` es el struct de Windows en tiempo de ejecución independiente del lenguaje para representar la información de tipo. [Platform::Type](../cppcx/platform-type-class.md) es específico de C++ y no se puede pasar a través de la interfaz binaria de aplicación (ABI). A continuación se muestra un uso de `TypeName`en la función [Navigate](http://msdn.microsoft.com/library/windows/apps/hh702394.aspx) :  
  
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
 [operador Windows::UI::Xaml::Interop::TypeName](../cppcx/operator-windows-ui-xaml-interop-typename.md)   
 [Platform::Type (Clase)](../cppcx/platform-type-class.md)