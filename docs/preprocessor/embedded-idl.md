---
title: embedded_idl | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- embedded_idl
dev_langs:
- C++
helpviewer_keywords:
- embedded_idl attribute
ms.assetid: f1c1c2e8-3872-4172-8795-8d1288a20452
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b8a93f71da7b7f0819b5a48af1541909037bbe65
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="embeddedidl"></a>embedded_idl
**C++ Specific**  
  
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