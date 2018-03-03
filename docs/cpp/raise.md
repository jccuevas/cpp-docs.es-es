---
title: __raise | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- __raise
- __raise_cpp
dev_langs:
- C++
helpviewer_keywords:
- __raise keyword [C++]
ms.assetid: 6f1ae418-5f0f-48b6-9f6e-8ea7e66b239a
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a59485af5532276a125b020213e2ce01212511d9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="raise"></a>__raise
Resalta el sitio de llamada de un evento.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
__raise   
method-declarator  
;  
  
```  
  
## <a name="remarks"></a>Comentarios  
 En código administrado, un evento solo se puede generar desde dentro de la clase donde se define. Vea [evento](../windows/event-cpp-component-extensions.md) para obtener más información.  
  
 La palabra clave `__raise` hace que se produzca un error si se llama a algún elemento que no es un evento.  
  
> [!NOTE]
>  Una clase o struct basada en plantilla no puede contener eventos.  
  
## <a name="example"></a>Ejemplo  
  
```  
// EventHandlingRef_raise.cpp  
struct E {  
   __event void func1();  
   void func1(int) {}  
  
   void func2() {}  
  
   void b() {  
      __raise func1();  
      __raise func1(1);  // C3745: 'int Event::bar(int)':   
                         // only an event can be 'raised'  
      __raise func2();   // C3745  
   }  
};  
  
int main() {  
   E e;  
   __raise e.func1();  
   __raise e.func1(1);  // C3745  
   __raise e.func2();   // C3745  
}  
```  
  
## <a name="see-also"></a>Vea también  
 [Palabras clave](../cpp/keywords-cpp.md)   
 [Control de eventos](../cpp/event-handling.md)   
 [Extensiones de componentes para plataformas de tiempo de ejecución](../windows/component-extensions-for-runtime-platforms.md)