---
title: __super | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-language
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- __super_cpp
dev_langs:
- C++
helpviewer_keywords:
- __super keyword [C++]
ms.assetid: f0957c31-9256-405b-b402-cad182404b5f
caps.latest.revision: 7
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 93585337ae34e7c95d1c11b0a970afc8b36987bb
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="super"></a>__super
**Específicos de Microsoft**  
  
 Permite establecer explícitamente que se está llamando a una implementación de la clase base para una función que se va a reemplazar.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
__super::  
member_function  
();  
  
```  
  
## <a name="remarks"></a>Comentarios  
 Todos los métodos accesibles de la clase base se consideran durante la fase de la resolución de sobrecarga y la función que proporciona la mejor coincidencia es la que se llama.  
  
 `__super` solo puede aparecer en el cuerpo de una función miembro.  
  
 `__super` no se puede utilizar con una declaración using. Vea [mediante declaración](../cpp/using-declaration.md) para obtener más información.  
  
 Con la introducción de [atributos](../windows/cpp-attributes-reference.md) que insertan código, el código podría contener una o más clases base cuyos nombres puede no conocer, pero que contienen métodos que desea llamar.  
  
## <a name="example"></a>Ejemplo  
  
```  
// deriv_super.cpp  
// compile with: /c  
struct B1 {  
   void mf(int) {}  
};  
  
struct B2 {  
   void mf(short) {}  
  
   void mf(char) {}  
};  
  
struct D : B1, B2 {  
   void mf(short) {  
      __super::mf(1);   // Calls B1::mf(int)  
      __super::mf('s');   // Calls B2::mf(char)  
   }  
};  
```  
  
 **FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [Palabras clave](../cpp/keywords-cpp.md)