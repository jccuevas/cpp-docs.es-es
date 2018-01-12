---
title: Error del compilador C3836 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3836
dev_langs: C++
helpviewer_keywords: C3836
ms.assetid: 254f851b-7b7d-4c34-a740-fcf72f6a636a
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ed48f6fd044ccc17dacd79d774f8db2c6888a0cd
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3836"></a>Error del compilador C3836
constructor estático no puede tener una lista de inicializadores de miembro  
  
 Una clase administrada no puede tener un constructor estático que también tiene una lista de inicialización de miembros. Constructores de clases estáticas son llamados por common language runtime para la inicialización, inicialización de los miembros de datos estáticos de clase.  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente genera C3836:  
  
```  
// C3836a.cpp  
// compile with: /clr  
ref class M  
{  
   static int s_i;  
  
public:  
   static M() :  s_i(1234)   // C3836, delete initializer to resolve  
   {  
   }  
};  
  
int main()  
{  
}  
```  
