---
title: 'Clase Platform:: Type | Documentos de Microsoft'
ms.custom: 
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::Type::GetTypeCode
- VCCORLIB/Platform::Type::FullName
dev_langs:
- C++
helpviewer_keywords:
- Platform::Type Class
ms.assetid: d6b03f1e-b240-49b9-a08e-53a460030475
caps.latest.revision: 
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: cabfa3d382d44448b2c06d0a16864a4fdd0e66bf
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
---
# <a name="platformtype-class"></a>Platform::Type (Clase)
Contiene información en tiempo de ejecución sobre un tipo, en concreto, un nombre de cadena y un typecode. Obtenido mediante una llamada a [Object:: GetType](../cppcx/platform-object-class.md#gettype) en cualquier objeto u o mediante el [typeid](../windows/typeid-cpp-component-extensions.md) operador en un nombre de clase o struct.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
public ref class Platform::Type :      
    Platform::Object, Platform::Details::IEquatable,
    Platform::Details::IPrintable  
```  
  
### <a name="remarks"></a>Comentarios  
 La clase `Type` es útil en aplicaciones que deben dirigir el procesamiento mediante una instrucción `if` o `switch` que se bifurca en función del tipo en tiempo de ejecución de un objeto. El código de tipo que describe la categoría de un tipo se recupera utilizando la [Type:: GetTypeCode](#gettypecode) función miembro.  
  
## <a name="public-methods"></a>Métodos públicos  
  
|||  
|-|-|  
|[método Type::GetTypeCode](#gettypecode)|Devuelve un valor de [enumeración Platform::TypeCode](../cppcx/platform-typecode-enumeration.md) para el objeto.| 
|[Type::ToString (método)](#tostring)|Devuelve el nombre del tipo de acuerdo con lo especificado en sus metadatos.| 

 
## <a name="public-properties"></a>Propiedades públicas  
  
|||  
|-|-|  
|[Type::FullName](#fullname)|Devuelve una [clase Platform::String](../cppcx/platform-string-class.md)^ que representa el nombre completo del tipo y usa . (punto) como separador, no:: (dos puntos), por ejemplo, `MyNamespace.MyClass`.|  
  
## <a name="conversion-operators"></a>Operadores de conversión  
  
|||  
|-|-|  
|[operador Type^](../cppcx/operator-subtracttype-hat.md)|Permite la conversión de `Windows::UI::Xaml::Interop::TypeName` a `Platform::Type`.|  
|[operator Windows::UI::Xaml::Interop::TypeName](../cppcx/operator-subtractwindows-ui-xaml-interop-typename.md)|Permite la conversión de `Platform::Type` a `Windows::UI::Xaml::Interop::TypeName`.|  
  
### <a name="requirements"></a>Requisitos  
 **Cliente mínimo admitido:** Windows 8  
  
 **Servidor mínimo admitido:** Windows Server 2012  
  
 **Espacio de nombres:** Plataforma  
  
 **Metadatos:** platform.winmd  

 
## <a name="fullname"></a> Type::FullName (Propiedad)
Recupera el nombre completo del tipo actual en el formulario `Namespace.Type`.  
  
### <a name="syntax"></a>Sintaxis  
  
```cpp  
String^ FullName();  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Nombre del tipo.  
### <a name="example"></a>Ejemplo  
  
```  
  
//  namespace is TestApp  
MainPage::MainPage()  
{  
    InitializeComponent();  
    Type^ t = this->GetType();  
    auto s = t->FullName; // returns "TestApp.MainPage"  
    auto s2 = t->ToString(); //also returns "TestApp.MainPage"  
}  
```  
  


## <a name="gettypecode"></a> método Type::GetTypeCode
Recupera una categoría de tipo numérico de tipos integrados.  
  
### <a name="syntax"></a>Sintaxis  
  
```cpp  
Platform::TypeCode GetTypeCode();  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Uno de los valores enumerados de Platform::TypeCode.  
  
### <a name="remarks"></a>Comentarios  
 El equivalente del método miembro GetTypeCode() es la `typeid` propiedad.

## <a name="tostring">Type::ToString (método)</a>
Recupera un el nombre del tipo.  
  
### <a name="syntax"></a>Sintaxis  
  
```cpp  
Platform::String^ ToString();  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un nombre del tipo de acuerdo con lo especificado en sus metadatos.    
  
## <a name="see-also"></a>Vea también  
 [Espacio de nombres de plataforma](../cppcx/platform-namespace-c-cx.md)