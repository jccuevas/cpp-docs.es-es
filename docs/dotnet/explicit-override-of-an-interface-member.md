---
title: Reemplazo explícito de un miembro de interfaz | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- virtual functions, explicit overrides
- overriding functions
- interface members, explicit overrides
- functions [C++], overriding
- explicit override of virtual function
ms.assetid: 46f1f536-bf43-4311-9a17-ff2282e528a9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 811112d2721edccede6c7b4a278189fdec874523
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33110451"
---
# <a name="explicit-override-of-an-interface-member"></a>Reemplazo explícito de un miembro de interfaz
La sintaxis para declarar un reemplazo explícito de un miembro de interfaz dentro de una clase ha cambiado de extensiones administradas para C++ a Visual C++.  
  
 A menudo desea proporcionar dos instancias de un miembro de interfaz dentro de una clase que implementa la interfaz: una que se utiliza cuando se manipulan objetos de clase mediante un identificador de interfaz y otra que se utiliza cuando se usan objetos de clase mediante la interfaz de clase. Por ejemplo:  
  
```  
public __gc class R : public ICloneable {  
   // to be used through ICloneable  
   Object* ICloneable::Clone();  
  
   // to be used through an R  
   R* Clone();  
};  
```  
  
 En extensiones administradas hacer esto proporcionando una declaración explícita del método de interfaz con el nombre del método calificado con el nombre de la interfaz. La instancia específica de la clase es unqualified. Esto elimina la necesidad de convertir el valor devuelto de `Clone`, en este ejemplo, cuando se le llama explícitamente a través de una instancia de `R`.  
  
 En la nueva sintaxis, se ha introducido un mecanismo reemplazo general que reemplaza la sintaxis de extensiones administradas. Nuestro ejemplo sería reescrito como sigue:  
  
```  
public ref class R : public ICloneable {  
public:  
   // to be used through ICloneable  
   virtual Object^ InterfaceClone() = ICloneable::Clone;  
  
   // to be used through an R  
   virtual R^ Clone();  
};  
```  
  
 Esta revisión requiere que se invalide explícitamente el miembro de interfaz puede proporcionar un nombre único dentro de la clase. En este caso, he proporcionado un nombre de `InterfaceClone`. El comportamiento es el mismo: una invocación a través de la `ICloneable` interfaz invoca cambiado `InterfaceClone`, mientras que una llamada a través de un objeto de tipo `R` invoca el segundo `Clone` instancia.  
  
## <a name="see-also"></a>Vea también  
 [Declaraciones de miembros en una clase o interfaz (C++ / CLI)](../dotnet/member-declarations-within-a-class-or-interface-cpp-cli.md)   
 [Invalidaciones explícitas](../windows/explicit-overrides-cpp-component-extensions.md)