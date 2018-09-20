---
title: Reemplazo explícito de un miembro de interfaz | Microsoft Docs
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
ms.openlocfilehash: 57c26c1185eff0e88e18ef23cb8506fb1fed407a
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46409030"
---
# <a name="explicit-override-of-an-interface-member"></a>Reemplazo explícito de un miembro de interfaz

La sintaxis para declarar un reemplazo explícito de un miembro de interfaz dentro de una clase ha cambiado de extensiones administradas para C++ a Visual C++.

A menudo desee proporcionar dos instancias de un miembro de interfaz dentro de una clase que implementa la interfaz: uno que se utiliza cuando se manipulan objetos de clase mediante un identificador de interfaz y que se usa cuando se usan objetos de clase a través de la interfaz de clase. Por ejemplo:

```
public __gc class R : public ICloneable {
   // to be used through ICloneable
   Object* ICloneable::Clone();

   // to be used through an R
   R* Clone();
};
```

En extensiones administradas hacemos esto proporcionando una declaración explícita del método de interfaz con el nombre del método calificado con el nombre de la interfaz. La instancia específica de la clase está incompleta. Esto elimina la necesidad de convertirlo en el valor devuelto de `Clone`, en este ejemplo, cuando se le llama explícitamente a través de una instancia de `R`.

En la nueva sintaxis, un mecanismo de reemplazo general se ha introducido que reemplaza la sintaxis de extensiones administradas. En nuestro ejemplo se podría reescribir como sigue:

```
public ref class R : public ICloneable {
public:
   // to be used through ICloneable
   virtual Object^ InterfaceClone() = ICloneable::Clone;

   // to be used through an R
   virtual R^ Clone();
};
```

Esta revisión requiere que sea el miembro de interfaz que se va a reemplazar explícitamente un nombre único dentro de la clase. En este caso, he proporcionado un nombre de `InterfaceClone`. El comportamiento es el mismo: una invocación a través de la `ICloneable` interfaz invoca cambiado `InterfaceClone`, mientras que una llamada a través de un objeto de tipo `R` invoca el segundo `Clone` instancia.

## <a name="see-also"></a>Vea también

[Declaraciones de miembros en una clase o interfaz (C++/CLI)](../dotnet/member-declarations-within-a-class-or-interface-cpp-cli.md)<br/>
[Invalidaciones explícitas](../windows/explicit-overrides-cpp-component-extensions.md)