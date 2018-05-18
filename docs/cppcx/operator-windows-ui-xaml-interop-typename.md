---
title: operador Windows::UI::Xaml::Interop::TypeName | Documentos de Microsoft
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: language-reference
ms.assetid: a65a105e-7e3a-452f-932f-2cdaf00fbba5
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 714d39a70b19998a5daddceadc2c91df65312122
ms.sourcegitcommit: 19a108b4b30e93a9ad5394844c798490cb3e2945
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/17/2018
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