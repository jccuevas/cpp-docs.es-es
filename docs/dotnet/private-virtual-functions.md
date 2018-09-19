---
title: Funciones virtuales privadas | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- virtual functions, private
- derived classes, virtual functions
- access modifiers [C++], for class members
- member access [C++], virtual members
ms.assetid: 04448086-bf72-44be-9c1f-dfda1744949e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 97b4d7d9f47901fa69aa50bfc6f405355cf378b8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33162343"
---
# <a name="private-virtual-functions"></a>Funciones virtuales privadas
La manera en que se controlan las funciones virtuales privadas en clases derivadas ha cambiado de extensiones administradas para C++ a Visual C++.  
  
 En extensiones administradas, el nivel de acceso de una función virtual no restringe su capacidad para que se invalide en una clase derivada. En la nueva sintaxis, una función virtual no puede reemplazar una función virtual de clase base que no tiene acceso. Por ejemplo:  
  
```  
__gc class MyBaseClass {  
   // inaccessible to a derived class   
   virtual void g();  
};  
  
__gc class MyDerivedClass : public MyBaseClass {  
public:  
   // okay in Managed Extensions; g() overrides MyBaseClass::g()  
   // error in new syntax; cannot override: MyBaseClass::g() is inaccessible  
   void g();  
};  
```  
  
 No hay ninguna asignación real de este tipo de diseño a la nueva sintaxis. Uno simplemente tiene que hacer los miembros de clase base accesible: es decir, no privados. Los métodos heredados no tiene que tener el mismo acceso. En este ejemplo, el cambio menos invasivo consiste en convertir el miembro MyBaseClass `protected`. Este modo acceso del programa general al método mediante MyBaseClass sigue estando prohibido.  
  
```  
ref class MyBaseClass {  
protected:  
   virtual void g();  
};  
  
ref class MyDerivedClass : MyBaseClass {  
public:  
   virtual void g() override;  
};  
```  
  
 Tenga en cuenta que la ausencia de la explícita `virtual` palabra clave en la clase base, en la nueva sintaxis, genera un mensaje de advertencia.  
  
## <a name="see-also"></a>Vea también  
 [Declaraciones de miembros en una clase o interfaz (C++/CLI)](../dotnet/member-declarations-within-a-class-or-interface-cpp-cli.md)   
 