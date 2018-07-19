---
title: Compilador advertencia (nivel 1) C4364 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4364
dev_langs:
- C++
helpviewer_keywords:
- C4364
ms.assetid: 1477634c-d60f-4570-ad16-1aaeae24ac7f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fb3bfb8075d618a6d2ea9b733b01d8b456fdc0e7
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33283766"
---
# <a name="compiler-warning-level-1-c4364"></a>Advertencia del compilador (nivel 1) C4364
\#para el ensamblado 'archivo' ya aparecía previamente en ubicación (número_de_línea) sin el atributo as_friend; as_friend que no se aplica  
  
 A `#using` directiva se repite en un archivo de metadatos determinado, pero la `as_friend` calificador no se utilizó en la primera aparición; el compilador ignorará el segundo `as_friend`.  
  
 Para obtener más información, consulte [ensamblados Friend (C++)](../../dotnet/friend-assemblies-cpp.md).  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se crea un componente.  
  
```  
// C4364.cpp  
// compile with: /clr /LD  
ref class A {};  
```  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente genera C4364.  
  
```  
// C4364_b.cpp  
// compile with: /clr /W1 /c  
#using " C4364.dll"  
#using " C4364.dll" as_friend   // C4364  
```