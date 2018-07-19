---
title: __super | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- __super_cpp
dev_langs:
- C++
helpviewer_keywords:
- __super keyword [C++]
ms.assetid: f0957c31-9256-405b-b402-cad182404b5f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b9caa3d08140887da45916b931b6a4850358db16
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/10/2018
ms.locfileid: "37944847"
---
# <a name="super"></a>__super
**Específicos de Microsoft**  
  
 Permite establecer explícitamente que se está llamando a una implementación de la clase base para una función que se va a reemplazar.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
__super::member_function();  
  
```  
  
## <a name="remarks"></a>Comentarios  
 Todos los métodos accesibles de la clase base se consideran durante la fase de la resolución de sobrecarga y la función que proporciona la mejor coincidencia es la que se llama.  
  
 **__super** solo puede aparecer dentro del cuerpo de una función miembro.  
  
 **__super** no se puede usar con el uso de una declaración. Consulte [mediante declaración](../cpp/using-declaration.md) para obtener más información.  
  
 Con la introducción de [atributos](../windows/cpp-attributes-reference.md) que insertan código, el código podría contener una o más clases bases cuyos nombres no puede conocer, pero que contienen métodos que desea llamar.  
  
## <a name="example"></a>Ejemplo  
  
```cpp 
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