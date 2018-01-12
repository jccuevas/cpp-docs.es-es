---
title: "Portabilidad en los límites de ABI (C++ moderno) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: abbd405e-3038-427c-8c24-e00598f0936a
caps.latest.revision: "4"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 06cb6c97580b4c4c9a6c961cb76f2c4d84d841ac
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="portability-at-abi-boundaries-modern-c"></a>Portabilidad en los límites de ABI (C++ moderno)
Usan convenciones y tipos lo suficientemente portables en los límites de la interfaz binaria. Un "tipo portátil" es un tipo integrado de C o un struct que contiene solo tipos integrados de C. Tipos de clase solo pueden usarse al llamador y destinatario equipos acuerdan el diseño, etcetera, de convención de llamada. Esto solo es posible si ambos se compilan con el mismo compilador y la configuración del compilador.  
  
## <a name="how-to-flatten-a-class-for-c-portability"></a>Cómo eliminar la estructura de una clase para la portabilidad de C  
 Cuando los autores de llamadas puede compilarse con otro compilador/idioma, a continuación, "acoplar" a un **extern "C"** API con una convención de llamada específica:  
  
```cpp  
// class widget {  
//   widget();  
//   ~widget();  
//   double method( int, gadget& );  
// };  
extern "C" {        // functions using explicit "this"  
   struct widget;   // opaque type (forward declaration only)  
   widget* STDCALL widget_create();      // constructor creates new "this"  
   void STDCALL widget_destroy(widget*); // destructor consumes "this"  
   double STDCALL widget_method(widget*, int, gadget*); // method uses "this"  
}  
```  
  
## <a name="see-also"></a>Vea también  
 [Aquí está otra vez C++](../cpp/welcome-back-to-cpp-modern-cpp.md)   
 [Referencia del lenguaje C++](../cpp/cpp-language-reference.md)   
 [Biblioteca estándar de C++](../standard-library/cpp-standard-library-reference.md)