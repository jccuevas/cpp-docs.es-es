---
title: Aplicaciones Windows universales (C++) | Documentos de Microsoft
ms.custom: ''
ms.date: 03/30/2018
ms.technology:
- cpp-windows
ms.topic: article
dev_langs:
- C++
ms.assetid: 357121cc-d390-4bae-b34a-39614861a9f4
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 142a9c8e7c25dc9eee559f973f4cbd61337581c0
ms.sourcegitcommit: 78e5e5cdbafd29e2a6ccf68d4cce215136952907
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/03/2018
---
# <a name="universal-windows-apps-c"></a>Aplicaciones Windows universales (C++)

Aplicaciones universales de plataforma de Windows (UWP) representan un conjunto de principios de diseño que crear interfaces de usuario simple que están centradas en el contenido que se ajusta automáticamente a los diferentes tamaños de pantalla en diversos dispositivos. La interfaz de usuario se crea en el marcado XAML y el código subyacente en C++ nativo. También puede crear componentes (archivos DLL) que las aplicaciones para UWP escritas en otros lenguajes pueden consumir. La superficie de API para aplicaciones UWP es el tiempo de ejecución de Windows, que es una biblioteca factorizada correctamente que proporciona una amplia variedad de servicios del sistema operativo.

> [!TIP]  
> Para Windows 10, puede utilizar el convertidor de aplicación de escritorio puente para empaquetar la aplicación de escritorio existente para la implementación a través de Microsoft Store. Para obtener más información, consulte [utilizando Visual C++ en tiempo de ejecución en el proyecto Centennial](https://blogs.msdn.microsoft.com/vcblog/2016/07/07/using-visual-c-runtime-in-centennial-project) y [Desktop puente](/windows/uwp/porting/desktop-to-uwp-root).

## <a name="uwp-apps-that-use-cwinrt"></a>Las aplicaciones UWP que usan C++ / WinRT

C++ / WinRT es una nueva, solo encabezado basada en la biblioteca C++ language proyección para el tiempo de ejecución de Windows que usa completamente estándar de C++, a diferencia de C + / implementación CX. C++ / WinRT no utiliza sintaxis no estándar o extensiones de lenguaje de Microsoft, y aprovecha al máximo el compilador de C++ para crear una salida más optimizado. Para obtener más información, consulte [C++ / WinRT](/windows/uwp/cpp-and-winrt-apis). Para obtener una introducción a C++ / WinRT y un inicio rápido de código, vea [Introducción a C++ / WinRT](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt).

## <a name="uwp-apps-that-use-ccx"></a>Las aplicaciones UWP que usan C++ / CX

|||
|-|-|
|[Referencia del lenguaje Visual C++ (C++/CX)](../cppcx/visual-c-language-reference-c-cx.md)|Describe el conjunto de extensiones que simplifican el uso de C++ de Windows Runtime APIs y habilitar el control de errores que se basa en excepciones.|
|[Compilar aplicaciones y bibliotecas (C++/CX)](../cppcx/building-apps-and-libraries-c-cx.md)|Describe cómo crear bibliotecas DLL y estáticas a las que se puede tener acceso desde una aplicación o componente de C++/CX.|
|[Tutorial: Crear un UWP aplicación "Hello, World" en C++ / CX](/windows/uwp/get-started/create-a-basic-windows-10-app-in-cpp)|Un tutorial que presenta los conceptos básicos de desarrollo de aplicaciones UWP en C++ / CX. |
|[Crear componentes de tiempo de ejecución de Windows en C++ / CX](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp)|Describe cómo crear bibliotecas DLL que pueden consumir otros componentes y aplicaciones UWP.|
|[Programación de juegos de UWP](/windows/uwp/gaming/)|Describe cómo utilizar DirectX y C++ / CX para crear juegos.|

## <a name="uwp-apps-that-use-the-windows-runtime-c-template-library-wrl"></a>Aplicaciones UWP que usan la biblioteca de plantillas C++ de Windows en tiempo de ejecución (WRL)

La biblioteca de plantillas de C++ de Windows en tiempo de ejecución proporciona interfaces COM de bajo nivel que el código ISO C++ puede tener acceso a Windows Runtime en un entorno sin excepciones. En la mayoría de los casos, recomendamos utilizar C++ / WinRT o C++ / CX en lugar de la biblioteca de plantillas de C++ de Windows en tiempo de ejecución para el desarrollo de la aplicación UWP. Para obtener información acerca de la biblioteca de plantillas de C++ de Windows en tiempo de ejecución, consulte [biblioteca de plantillas de C++ (WRL) de Windows en tiempo de ejecución](../windows/windows-runtime-cpp-template-library-wrl.md).

## <a name="see-also"></a>Vea también

[Visual C++](../visual-cpp-in-visual-studio.md)<br/>
