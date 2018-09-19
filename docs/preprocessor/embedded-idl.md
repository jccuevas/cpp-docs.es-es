---
title: embedded_idl | Microsoft Docs
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
ms.openlocfilehash: b41af8375249a48ac3a866af224370b19f071d28
ms.sourcegitcommit: d4c803bd3a684d7951bf88dcecf1f14af43ae411
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/10/2018
ms.locfileid: "42538499"
---
# <a name="embeddedidl"></a>embedded_idl
**Específicos de C++**  
  
Especifica que la biblioteca de tipos se escriba en el archivo .tlh, conservando el código generado por el atributo.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
embedded_idl[("param")]  
```  
  
### <a name="parameters"></a>Parámetros  
*param*  
Puede ser uno de dos valores:  
  
- emitidl: la información de tipo importada de typelib estará presente en el archivo IDL generado para el proyecto con atributos.  Este es el valor predeterminado y estará en vigor si no se especifica un parámetro para `embedded_idl`.  
  
- no_emitidl: la información de tipo importada de typelib no estará presente en el archivo IDL generado para el proyecto con atributos.  
  
## <a name="example"></a>Ejemplo  
  
```cpp  
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
[directiva #import](../preprocessor/hash-import-directive-cpp.md)