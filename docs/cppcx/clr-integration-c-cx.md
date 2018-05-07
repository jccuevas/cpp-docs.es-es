---
title: Integración de CLR (C++ / CX) | Documentos de Microsoft
ms.custom: ''
ms.date: 01/22/2017
ms.technology: cpp-windows
ms.topic: language-reference
ms.assetid: 76e213cf-2f3d-4181-b35b-9fd25d5b307c
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 50b455bd3b6fd4a96c3181b60904cb7a3250e866
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="clr-integration-ccx"></a>Integración de CLR (C++/CX)
Algunos tipos de Windows en tiempo de ejecución reciben un tratamiento especial en C++ / CX y los idiomas que se basan en common language runtime (CLR). En este artículo se describe la manera en que varios tipos de un lenguaje se asignan a otro lenguaje. Por ejemplo, CLR asigna Windows.Foundation.IVector to System.Collections.IList, Windows.Foundation.IMap to System.Collections.IDictionary, etc. De forma similar, C++ / CX asigna especialmente tipos como Platform:: Delegate y Platform:: String.  
  
## <a name="mapping-the-windows-runtime-to-ccx"></a>Asignación de Windows Runtime c++ / CX  
 Cuando C++ / CX lee un archivo de metadatos (.winmd) de Windows, el compilador asigna automáticamente espacios de nombres comunes de Windows Runtime y tipos de c++ / CX espacios de nombres y tipos. Por ejemplo, el tipo en tiempo de ejecución de Windows numérico `UInt32` se asignan automáticamente a `default::uint32`.  
  
 C++ / CX asigna varios otros tipos en tiempo de ejecución de Windows para la **plataforma** espacio de nombres. Por ejemplo, el **Windows::Foundation** controlador HSTRING, que representa una cadena de texto Unicode de solo lectura, se asigna a C++ / CX `Platform::String` clase. Cuando una operación de Windows Runtime devuelve un HRESULT de error, se asigna a C++ / CX `Platform::Exception`. Para obtener más información, consulta [Built-in Types](http://msdn.microsoft.com/en-us/acc196fd-09da-4882-b554-6c94685ec75f).  
  
 C++ / CX también asigna determinados tipos de espacios de nombres en tiempo de ejecución de Windows para mejorar la funcionalidad del tipo. Para estos tipos, C++ / CX proporciona constructores auxiliares y métodos que son específicas de C++ y no están disponibles en el archivo de .winmd estándar del tipo.  
  
 En las listas siguientes se muestran estructuras de valor que admiten nuevos métodos auxiliares y constructores. Si ha escrito código anteriormente que usa listas de inicialización de estructuras, cámbielo para usar los constructores recién agregados.  
  
 **Windows::Foundation**  
  
-   Punto  
  
-   Rect  
  
-   Tamaño  
  
 **Windows::UI**  
  
-   Color  
  
 **Windows::UI::XAML**  
  
-   CornerRadius  
  
-   Duración  
  
-   GridLength  
  
-   Thickness  
  
 **Windows::UI::XAML::Interop**  
  
1.  TypeName  
  
 **Windows::UI::Xaml::Media**  
  
-   Matrix  
  
 **Windows::UI::XAML::Media::Animation**  
  
-   KeyTime  
  
-   RepeatBehavior  
  
 **Windows::UI::Xaml::Media::Media3D**  
  
-   Matrix3D  
  
## <a name="mapping-the-clr-to-ccx"></a>Asignación de CLR en C++ / CX  
 Cuando los compiladores de C# o Visual C++ leen un archivo .winmd, asignan automáticamente determinados tipos en el archivo de metadatos adecuado c++ / CX o CLR de tipos. Por ejemplo, en el CLR, la IVector\<T > interfaz se asigna a IList\<T >. Pero en C++ / CX, el IVector\<T > interfaz no está asignada a otro tipo.  
  
 IReference\<T > en el tiempo de ejecución de Windows se asigna a Nullable\<T > en. NET.  
  
## <a name="see-also"></a>Vea también  
 [Interoperar con otros lenguajes](../cppcx/interoperating-with-other-languages-c-cx.md)