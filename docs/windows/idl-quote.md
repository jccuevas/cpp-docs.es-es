---
title: idl_quote | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- vc-attr.idl_quote
dev_langs:
- C++
helpviewer_keywords:
- idl_quote attribute
ms.assetid: a370e1b7-948b-4e67-9a25-58facf24e4c9
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 288d90bf2e32024792eaf5ec44825a9ac992bd71
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="idlquote"></a>idl_quote
Le permite usar las construcciones de IDL no se admiten en la versión actual de Visual C++ y pídale que pasen al archivo .idl generado.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
      [ idl_quote(  
   text  
) ]  
```  
  
#### <a name="parameters"></a>Parámetros  
 *texto*  
 Nombre del atributo que desea que el compilador de Visual C++ que pasen al archivo .idl generado sin devolver un error del compilador.  
  
## <a name="remarks"></a>Comentarios  
 Si el **idl_quote** atributo de C++ se utiliza como un atributo independiente (con un punto y coma después del corchete de cierre), a continuación, *texto* se coloca en el archivo .idl combinada tal cual. Si **idl_quote** se utiliza en un símbolo, *texto* se coloca en el bloque de atributos de ese símbolo.  
  
## <a name="example"></a>Ejemplo  
 El código siguiente muestra cómo puede especificar un atributo no admitido (mediante **en**, que se admite) y cómo definir y utilizar una construcción .idl sin definir:  
  
```  
// cpp_attr_ref_idl_quote.cpp  
// compile with: /LD  
#include <unknwn.h>  
[module(name="MyLibrary")];  
  
[export]  
struct MYFLOT {  
   int i;  
};  
  
[export]  
struct MYDUB {  
   int i;  
};  
  
[idl_quote("typedef union _S1_TYPE switch (long l1) U1_TYPE { case 1024: \  
struct MYFLOT f1; case 2048: struct MYDUB d2; } S1_TYPE;") ];  
  
typedef struct _S1_TYPE {   
   long l1;   
  
union {   
   MYFLOT f1; MYDUB d2; } U1_TYPE;   
} S1_TYPE;  
  
[uuid("2F5F63F1-16DA-11d2-9E7B-00C04FB926DA"), object]  
__interface IStatic{  
   HRESULT Func1([idl_quote("in")] int i);  
   HRESULT func( S1_TYPE* myStruct );  
};  
```  
  
 Este código hace MYFLOT y MYDUB y *texto* entrada que se colocarán en el archivo .idl generado. El *nombre* parámetro fuerza *texto* para situarse antes de todo lo que hace referencia a *nombre* en el archivo .idl generado. El *dependencias* parámetro fuerza las definiciones de lista de dependencia deben colocarse antes de *texto* en el archivo .idl generado.  
  
## <a name="requirements"></a>Requisitos  
  
### <a name="attribute-context"></a>Contexto de atributo  
  
|||  
|-|-|  
|**Se aplica a**|En cualquier lugar|  
|**Reiterativo**|No|  
|**Atributos requeridos**|Ninguna|  
|**Atributos no válidos**|Ninguna|  
  
 Para obtener más información, vea [Contextos de atributo](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Vea también  
 [Atributos IDL](../windows/idl-attributes.md)   
 [Atributos independientes](../windows/stand-alone-attributes.md)   
