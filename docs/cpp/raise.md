---
title: __raise | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- __raise
- __raise_cpp
dev_langs:
- C++
helpviewer_keywords:
- __raise keyword [C++]
ms.assetid: 6f1ae418-5f0f-48b6-9f6e-8ea7e66b239a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 93bd00c89df69d655f42c06509ef0360eff0c092
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
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