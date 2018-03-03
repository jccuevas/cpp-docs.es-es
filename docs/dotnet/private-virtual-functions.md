---
title: Funciones virtuales privadas | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- virtual functions, private
- derived classes, virtual functions
- access modifiers [C++], for class members
- member access [C++], virtual members
ms.assetid: 04448086-bf72-44be-9c1f-dfda1744949e
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 9b407bc469a345706f99cf5bad578f678e652a4c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
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
 