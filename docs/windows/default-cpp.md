---
title: "default (C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "vc-attr.default"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "atributo predeterminado"
  - "atributos [C#], atributo default"
  - "valores predeterminados, atributo default"
ms.assetid: 0cdca716-1ba8-46d7-9399-167e55492870
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# default (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Indica que la interfaz personalizada o dispinterface definida en una coclase representa la interfaz de programación predeterminada.  
  
## Sintaxis  
  
```  
  
[ default(  
interface1  
,  
   interface2  
) ]  
  
```  
  
#### Parámetros  
 *interface1*  
 Interfaz predeterminada que estará disponible para los entornos de scripting que crean un objeto basado en la clase definida con el atributo **default**.  
  
 Si no se especifica ninguna interfaz predeterminada, se usa la primera aparición de una interfaz sin origen como valor predeterminado.  
  
 *interface2* \(opcional\)  
 Interfaz de origen predeterminada. También debe especificar esta interfaz con el atributo [source](../Topic/source%20\(C++\).md).  
  
 Si no se especifica ninguna interfaz de origen predeterminada, se usa la primera interfaz de origen como valor predeterminado.  
  
## Comentarios  
 El atributo C\+\+ **default** tiene la misma funcionalidad que el atributo MIDL [default](http://msdn.microsoft.com/library/windows/desktop/aa366787). El atributo **default** también se usa con el atributo [case](../windows/case-cpp.md).  
  
## Ejemplo  
 El siguiente código muestra cómo se usa **default** en la definición de una coclase para especificar **ICustomDispatch** como la interfaz de programación predeterminada:  
  
```  
// cpp_attr_ref_default.cpp  
// compile with: /LD  
#include "windows.h"  
[module(name="MyLibrary")];  
  
[object, uuid("9E66A290-4365-11D2-A997-00C04FA37DDB")]  
__interface ICustom {  
   HRESULT Custom([in] long l, [out, retval] long *pLong);  
};  
  
[dual, uuid("9E66A291-4365-11D2-A997-00C04FA37DDB")]   
__interface IDual {  
   HRESULT Dual([in] long l, [out, retval] long *pLong);  
};  
  
[object, uuid("9E66A293-4365-11D2-A997-00C04FA37DDB")]  
__interface ICustomDispatch : public IDispatch {  
   HRESULT Dispatch([in] long l, [out, retval] long *pLong);  
};  
  
[   coclass,  
   default(ICustomDispatch),   
   source(IDual),  
   uuid("9E66A294-4365-11D2-A997-00C04FA37DDB")  
]  
class CClass : public ICustom, public IDual, public ICustomDispatch {  
   HRESULT Custom(long l, long *pLong) { return(S_OK); }  
   HRESULT Dual(long l, long *pLong) { return(S_OK); }  
   HRESULT Dispatch(long l, long *pLong) { return(S_OK); }  
};  
  
int main() {  
#if 0 // Can't instantiate without implementations of IUnknown/IDispatch  
   CClass *pClass = new CClass;  
  
   long llong;  
  
   pClass->custom(1, &llong);  
   pClass->dual(1, &llong);  
   pClass->dispinterface(1, &llong);  
   pClass->dispatch(1, &llong);  
  
   delete pClass;  
#endif  
   return(0);  
}  
```  
  
 El atributo [source](../Topic/source%20\(C++\).md) también tiene un ejemplo de cómo usar **default**.  
  
## Requisitos  
  
### Contexto de atributo  
  
|||  
|-|-|  
|**Se aplica a**|**clase**, `struct`, miembro de datos|  
|**Reiterativo**|No|  
|**Atributos requeridos**|**coclase** \(cuando se aplica a **clase** o `struct`\)|  
|**Atributos no válidos**|Ninguna|  
  
 Para obtener más información, vea [Contextos de atributo](../windows/attribute-contexts.md).  
  
## Vea también  
 [IDL Attributes](../windows/idl-attributes.md)   
 [Class Attributes](../windows/class-attributes.md)   
 [coclass](../windows/coclass.md)   
 [Attributes Samples](http://msdn.microsoft.com/es-es/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)