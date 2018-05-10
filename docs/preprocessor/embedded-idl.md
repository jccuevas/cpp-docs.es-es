---
title: embedded_idl | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- embedded_idl
dev_langs:
- C++
helpviewer_keywords:
- embedded_idl attribute
ms.assetid: f1c1c2e8-3872-4172-8795-8d1288a20452
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1e0b594952e8e5be0a9be9c843877c8c4bb95eca
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
---
# <a name="embeddedidl"></a>embedded_idl
**Específicos de C++**  
  
 Especifica que la biblioteca de tipos se escriba en el archivo .tlh, conservando el código generado por el atributo.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
embedded_idl[("param")]  
```  
  
#### <a name="parameters"></a>Parámetros  
 `param`  
 Puede ser uno de dos valores:  
  
-   emitidl: la información de tipo importada de typelib estará presente en el archivo IDL generado para el proyecto con atributos.  Este es el valor predeterminado y estará en vigor si no se especifica un parámetro para `embedded_idl`.  
  
-   no_emitidl: la información de tipo importada de typelib no estará presente en el archivo IDL generado para el proyecto con atributos.  
  
## <a name="example"></a>Ejemplo  
  
```  
// import_embedded_idl.cpp  
// compile with: /LD  
#include <windows.h>  
[module(name="MyLib2")];  
#import "\school\bin\importlib.tlb" embedded_idl("no_emitidl")  
```  
  
## <a name="remarks"></a>Comentarios  
 **FIN de específicos de C++**  
  
## <a name="see-also"></a>Vea también  
 [atributos #import](../preprocessor/hash-import-attributes-cpp.md)   
 [#import (directiva)](../preprocessor/hash-import-directive-cpp.md)