---
title: Aplicaciones Windows universales (C++) | Documentos de Microsoft
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
ms.assetid: 357121cc-d390-4bae-b34a-39614861a9f4
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a293f833de7bc575209089362bcaf146d074684b
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
---
# <a name="universal-windows-apps-c"></a>Aplicaciones Windows universales (C++)
Aplicaciones universales de plataforma de Windows (UWP) representan un conjunto de principios de diseño que crear interfaces de usuario simple que están centradas en el contenido que se ajusta automáticamente a los diferentes tamaños de pantalla en diversos dispositivos. La interfaz de usuario se crea en el marcado XAML y el código subyacente en C++ nativo. También puede crear componentes (archivos DLL) que las aplicaciones para UWP escritas en otros lenguajes pueden consumir. La superficie de API para aplicaciones UWP es el tiempo de ejecución de Windows, que es una biblioteca factorizada correctamente que proporciona una amplia variedad de servicios del sistema operativo.  

> [!TIP]  
> Para Windows 10, puede utilizar el convertidor de la aplicación de escritorio para empaquetar la aplicación de escritorio existente para la implementación a través de Microsoft Store. Para obtener más información, vea [Using Visual C++ Runtime in Centennial project](https://blogs.msdn.microsoft.com/vcblog/2016/07/07/using-visual-c-runtime-in-centennial-project) (Usar el tiempo de ejecución de Visual C++ en el proyecto Centennial) y [Convertir la aplicación de escritorio en una aplicación para Plataforma universal de Windows (UWP) con el puente de escritorio](https://msdn.microsoft.com/en-us/windows/uwp/porting/desktop-to-uwp-root).
  
  
## <a name="uwp-apps-that-use-ccx"></a>Aplicaciones para UWP que usan C++/CX  
  
|||  
|-|-|  
|[Referencia del lenguaje Visual C++ (C++/CX)](../cppcx/visual-c-language-reference-c-cx.md)|Describe el conjunto de extensiones que simplifican el uso de C++ de Windows Runtime APIs y habilitar el control de errores que se basa en excepciones.|  
|[Compilar aplicaciones y bibliotecas (C++/CX)](../cppcx/building-apps-and-libraries-c-cx.md)|Describe cómo crear bibliotecas DLL y estáticas a las que se puede tener acceso desde una aplicación o componente de C++/CX.|  
|[Tutorial: Crear la primera aplicación UWP con C++](https://docs.microsoft.com/en-us/windows/uwp/get-started/create-a-basic-windows-10-app-in-cpp)|Un tutorial que presenta los conceptos básicos de desarrollo de aplicaciones UWP en C++. (Aún no se ha actualizado para el desarrollo de UWP en Windows 10).|  
|[Crear componentes de Windows en tiempo de ejecución en C++](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp)|Describe cómo crear bibliotecas DLL que pueden consumir otros componentes y aplicaciones UWP.|  
|[Desarrollar juegos](https://docs.microsoft.com/en-us/windows/uwp/gaming/)|Describe cómo utilizar DirectX y C++ para crear juegos.|  
  
## <a name="uwp-apps-that-use-the-windows-runtime-c-template-library-wrl"></a>Aplicaciones UWP que usan la biblioteca de plantillas C++ de Windows en tiempo de ejecución (WRL) 
 La biblioteca de plantillas de C++ de Windows en tiempo de ejecución proporciona interfaces COM de bajo nivel que el código ISO C++ puede tener acceso a Windows Runtime en un entorno sin excepciones. En la mayoría de los casos, recomendamos utilizar C++ / CX en lugar de la biblioteca de plantillas de C++ de Windows en tiempo de ejecución para el desarrollo de la aplicación UWP. Para obtener información acerca de la biblioteca de plantillas de C++ de Windows en tiempo de ejecución, consulte [biblioteca de plantillas de C++ (WRL) de Windows en tiempo de ejecución](../windows/windows-runtime-cpp-template-library-wrl.md).  
  
## <a name="see-also"></a>Vea también  
 [Visual C++](../visual-cpp-in-visual-studio.md)

