---
title: Pimpl para encapsulación en tiempo de compilación (C++ moderno) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: c3e8a90a-b328-4990-82bb-e1b147f76e07
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f611a898018cee5edc031be1db2fd35af8857e16
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32420160"
---
# <a name="pimpl-for-compile-time-encapsulation-modern-c"></a>Pimpl para encapsulación en tiempo de compilación (C++ moderno)
El *pimpl locución* es una técnica de C++ moderna para ocultar la implementación, para minimizar el acoplamiento and para separar interfaces. Pimpl es la abreviatura de "puntero a la implementación". Ya puede estar familiarizado con el concepto, pero saber por otros nombres como expresión sonrisa Cat o Firewall de compilador.  
  
## <a name="why-use-pimpl"></a>¿Por qué usar pimpl?  
 Esta es la forma en que la expresión pimpl puede mejorar el ciclo de vida de desarrollo de software:  
  
-   Minimización de dependencias de compilación.  
  
-   Separación de interfaz y la implementación.  
  
-   Portabilidad.  
  
## <a name="pimpl-header"></a>Encabezado Pimpl  
  
```cpp  
// my_class.h  
class my_class {  
   //  ... all public and protected stuff goes here ...  
private:  
   class impl; unique_ptr<impl> pimpl; // opaque type here  
};  
  
```  
  
 La expresión pimpl evita cascadas de regeneración y diseños de objeto complicado. También es ideal para los tipos conocidos (de manera transitiva).  
  
## <a name="pimpl-implementation"></a>Implementación de Pimpl  
 Definir la `impl` clase en el archivo .cpp.  
  
```cpp  
// my_class.cpp  
class my_class::impl {  // defined privately here  
  // ... all private data and functions: all of these  
  //     can now change without recompiling callers ...  
};  
my_class::my_class(): pimpl( new impl )  
{  
  // ... set impl values ...   
}  
```  
  
## <a name="best-practices"></a>Procedimientos recomendados  
 Considere la posibilidad de agregar compatibilidad para la especialización de intercambio no produce excepciones.  
  
## <a name="see-also"></a>Vea también  
 [Aquí está otra vez C++](../cpp/welcome-back-to-cpp-modern-cpp.md)   
 [Referencia del lenguaje C++](../cpp/cpp-language-reference.md)   
 [Biblioteca estándar de C++](../standard-library/cpp-standard-library-reference.md)