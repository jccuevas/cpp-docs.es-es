---
title: Aplicaciones Windows universales (C++)
ms.date: 03/30/2018
ms.assetid: 357121cc-d390-4bae-b34a-39614861a9f4
ms.topic: landing-page
ms.openlocfilehash: 6c2bf7e44e3f1cb2c73ccaaed4363e34cbd7f0c9
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/03/2019
ms.locfileid: "70218368"
---
# <a name="universal-windows-apps-c"></a>Aplicaciones Windows universales (C++)

El Plataforma universal de Windows (UWP) es la interfaz de programación moderna para Windows. Con UWP, escribirá una aplicación o un componente una vez e implementará en cualquier dispositivo de Windows 10. Puede escribir un componente en C++ y las aplicaciones escritas en cualquier otro lenguaje compatible con UWP pueden usarlo.

La mayoría de la documentación de UWP está en el árbol de contenido de Windows en [plataforma universal de Windows documentación](/windows/uwp/). Allí encontrará tutoriales de inicio y documentación de referencia. 

En el caso de las nuevas aplicaciones y componentes de UWP, se recomienda usar [ C++/WinRT](/windows/uwp/cpp-and-winrt-apis/), una nueva proyección de lenguaje estándar de c++ 17 para API de Windows Runtime. C++/WinRT está disponible en el SDK de Windows 10 de la versión 1803 en adelante. C++/WinRT se implementa completamente en los archivos de encabezado y está diseñado para proporcionarle acceso de primera clase a la API moderna de Windows. A diferencia de C++la implementación de/CX. C++/WinRT no usa sintaxis no estándar o extensiones de lenguaje de Microsoft, y aprovecha al máximo el C++ compilador para crear resultados muy optimizados. Para obtener más información, vea [Introducción C++a/WinRT](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt).

Puede usar el convertidor de aplicaciones de puente de escritorio para empaquetar la aplicación de escritorio existente para su implementación a través del Microsoft Store. Para obtener más información, consulte [uso C++ de Visual Runtime en el proyecto Centennial](https://blogs.msdn.microsoft.com/vcblog/2016/07/07/using-visual-c-runtime-in-centennial-project) y [puente de escritorio](/windows/uwp/porting/desktop-to-uwp-root).

## <a name="uwp-apps-that-use-ccx"></a>Aplicaciones para UWP que C++usan/CX

|||
|-|-|
|[Referencia del lenguaje Visual C++ (C++/CX)](visual-c-language-reference-c-cx.md)|Describe el conjunto de extensiones que simplifican C++ el consumo de Windows Runtime API y permiten el control de errores basado en excepciones.|
|[Compilar aplicaciones y bibliotecas (C++/CX)](building-apps-and-libraries-c-cx.md)|Describe cómo crear bibliotecas DLL y estáticas a las que se puede tener acceso desde una aplicación o componente de C++/CX.|
|[Tutorial: Crear una aplicación "Hello, World" de UWP C++en/CX](/windows/uwp/get-started/create-a-basic-windows-10-app-in-cpp)|Un tutorial que presenta los conceptos básicos del desarrollo de aplicaciones para C++UWP en/CX. |
|[Creación de componentes de C++Windows Runtime en/CX](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp)|Describe cómo crear archivos DLL que pueden consumir otras aplicaciones y componentes de UWP.|
|[Programación de juegos para UWP](/windows/uwp/gaming/)|Describe cómo usar DirectX y C++/CX para crear juegos.|

## <a name="uwp-apps-that-use-the-windows-runtime-c-template-library-wrl"></a>Aplicaciones para UWP que usan la C++ biblioteca de plantillas de Windows Runtime (WRL)

La biblioteca C++ de plantillas de Windows Runtime proporciona interfaces com de bajo nivel por las C++ que el código ISO puede tener acceso al Windows Runtime en un entorno sin excepciones. En la mayoría de los casos, se recomienda C++usar/WinRT C++o/CX en lugar de la C++ biblioteca de plantillas Windows Runtime para el desarrollo de aplicaciones para UWP. Para obtener información sobre la C++ biblioteca de plantillas de Windows Runtime, vea [Windows Runtime C++ Template Library (WRL)](wrl/windows-runtime-cpp-template-library-wrl.md).

## <a name="see-also"></a>Vea también

[C++ en Visual Studio](../overview/visual-cpp-in-visual-studio.md)<br/>
[Información general de la programación para Windows en C++](../windows/overview-of-windows-programming-in-cpp.md)<br/>