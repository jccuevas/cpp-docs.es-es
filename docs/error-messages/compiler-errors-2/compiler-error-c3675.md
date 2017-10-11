---
title: Error del compilador C3675 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3675
dev_langs:
- C++
helpviewer_keywords:
- C3675
ms.assetid: 87461613-6633-430b-b95d-c7cb1bb63776
caps.latest.revision: 5
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: d45236fc32fd0d10e9617b6946683d8ebd73ef0e
ms.contentlocale: es-es
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c3675"></a>Error del compilador C3675
'función': se ha reservado porque 'propiedad' está definido  
  
 Cuando se declara una propiedad simple, el compilador genera get y métodos de descriptor de acceso set y los nombres están presentes en el ámbito del programa.  Los nombres generados por el compilador se forman anteponiendo get_ y set_ al nombre de propiedad.  Por lo tanto, no puede declarar funciones con el mismo nombre que los descriptores de acceso generados por el compilador.  
  
 Vea [property](../../windows/property-cpp-component-extensions.md) para obtener más información.  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente genera C3675.  
  
```  
// C3675.cpp  
// compile with: /clr /c  
ref struct C {  
public:  
   property int Size;  
   int get_Size() { return 0; }   // C3675  
};  
```
