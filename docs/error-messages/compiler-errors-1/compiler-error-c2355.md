---
title: Error del compilador C2355 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2355
dev_langs: C++
helpviewer_keywords: C2355
ms.assetid: 0a947881-d61f-4f98-8409-32140f39500b
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 3060f97645061e0244091b416dcdfeef343f90b7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2355"></a>Error del compilador C2355
'this': solo se puede hacer referencia a this en funciones miembro no estáticas o inicializadores de miembro de datos no estáticos  
  
 El puntero `this` solo es válido en funciones miembro no estáticas o en inicializadores de miembro de datos no estáticos. Este error puede producirse si el ámbito de clase de una definición de función miembro fuera de la declaración de clase no está calificado correctamente. El error también puede producirse si el puntero `this` se utiliza en una función que no se haya declarado en la clase.  
  
 Para corregir este problema, asegúrese de que la definición de función miembro coincida con una declaración de función miembro de la clase y que no se haya declarado como estática. En los inicializadores de miembro de datos, asegúrese de que el miembro de datos no se haya declarado como estático.  
  
 El ejemplo siguiente genera el error C2355 y muestra cómo corregirlo:  
  
```  
// C2355.cpp  
// compile with: /c  
class MyClass {};  
MyClass *p = this;   // C2355  
  
// OK  
class MyClass2 {  
public:  
   void Test() {  
      MyClass2 *p = this;  
   }  
};  
```