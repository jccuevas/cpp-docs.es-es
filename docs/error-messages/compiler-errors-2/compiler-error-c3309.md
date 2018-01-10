---
title: Error del compilador C3309 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C3309
dev_langs: C++
helpviewer_keywords: C3309
ms.assetid: 75ee16e3-7d4e-4c41-b3cb-64e9849c3aab
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 4658e5ac1ebf96d87095f363d1842be876c9d4be
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3309"></a>Error del compilador C3309
'macro_name': el nombre de módulo no puede ser una macro ni una palabra clave  
  
 El valor que se pasa a la propiedad name del atributo de módulo no puede ser un símbolo para que el preprocesador se expanda; debe ser un literal de cadena.  
  
 El ejemplo siguiente genera la advertencia C3309:  
  
```  
// C3309.cpp  
#define NAME MyModule  
[module(name="NAME")];   // C3309  
// Try the following line instead  
// [module(name="MyModule")];  
[coclass]  
class MyClass {  
public:  
   void MyFunc();  
};  
  
int main() {  
}  
```