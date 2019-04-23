---
title: Aplicaciones Windows universales (C++)
ms.date: 03/30/2018
ms.assetid: 357121cc-d390-4bae-b34a-39614861a9f4
ms.openlocfilehash: fbd5366ee52dfe32baef9458a82c16914666699e
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "58785785"
---
# <a name="universal-windows-apps-c"></a>Aplicaciones Windows universales (C++)

La plataforma Universal de Windows (UWP) es la interfaz de programación moderna para Windows. Con UWP escribe una vez de la aplicación o componente e implementarlo en cualquier dispositivo Windows 10. Puede escribir un componente en C++ y las aplicaciones escritas en cualquier otro lenguaje compatible con UWP pueden usarla.

La mayoría de la documentación de UWP se encuentra en el árbol de contenido de Windows en [documentación de la plataforma Universal de Windows](/windows/uwp/). Allí encontrará tutoriales de inicio, así como documentación de referencia. 

Para nuevas aplicaciones UWP y componentes, recomendamos que use [C++ / c++ / WinRT](/windows/uwp/cpp-and-winrt-apis/), una nuevo estándar C ++ 17 proyección del lenguaje para Windows Runtime APIs. C++ / c++ / WinRT está disponible en el SDK de Windows 10 desde la versión 1803 en adelante. C++ / c++ / WinRT se implementa completamente en archivos de encabezado y está diseñado para proporcionarle acceso de primera clase a la API de Windows moderna. A diferencia de C++ / c++ / implementación de CX. C++ / c++ / WinRT no usa una sintaxis no estándar o extensiones de lenguaje de Microsoft y aprovecha plenamente el compilador de C++ para crear la salida altamente optimizada. Para obtener más información, consulte [Introducción a C++ / c++ / WinRT](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt).

Puede utilizar el convertidor de aplicación de puente de escritorio para empaquetar la aplicación de escritorio existente para la implementación a través de la Microsoft Store. Para obtener más información, consulte [utilizando Visual C++ en tiempo de ejecución en el proyecto Centennial](https://blogs.msdn.microsoft.com/vcblog/2016/07/07/using-visual-c-runtime-in-centennial-project) y [Desktop Bridge](/windows/uwp/porting/desktop-to-uwp-root).

## <a name="uwp-apps-that-use-ccx"></a>Las aplicaciones UWP que usan C++ / c++ / CX

|||
|-|-|
|[Referencia del lenguaje Visual C++ (C++/CX)](visual-c-language-reference-c-cx.md)|Describe el conjunto de extensiones que simplifican el uso de C++ de Windows Runtime APIs y habilitar el control de errores que se basa en excepciones.|
|[Compilar aplicaciones y bibliotecas (C++/CX)](building-apps-and-libraries-c-cx.md)|Describe cómo crear bibliotecas DLL y estáticas a las que se puede tener acceso desde una aplicación o componente de C++/CX.|
|[Tutorial: Creación de una UWP aplicación "Hello, World" en C / c++ / CX](/windows/uwp/get-started/create-a-basic-windows-10-app-in-cpp)|Un tutorial que presenta los conceptos básicos del desarrollo de aplicaciones UWP en C++ / c++ / CX. |
|[Creación de componentes de Windows Runtime en C++ / c++ / CX](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp)|Describe cómo crear archivos DLL que pueden consumir otras aplicaciones para UWP y componentes.|
|[Programación de juegos de UWP](/windows/uwp/gaming/)|Describe cómo utilizar DirectX y C++ / c++ / CX para crear juegos.|

## <a name="uwp-apps-that-use-the-windows-runtime-c-template-library-wrl"></a>Aplicaciones UWP que usan la biblioteca de plantillas C++ de Windows en tiempo de ejecución (WRL)

La biblioteca de plantillas C++ de Windows en tiempo de ejecución proporciona las interfaces de COM de bajo nivel mediante el cual puede tener acceso a código ISO C++ en tiempo de ejecución de Windows en un entorno sin excepciones. En la mayoría de los casos, se recomienda usar C++ / c++ / WinRT o C++ / c++ / CX en lugar de la biblioteca de plantillas de C++ de Windows en tiempo de ejecución para el desarrollo de aplicaciones UWP. Para obtener información acerca de la biblioteca de plantillas C++ de Windows en tiempo de ejecución, vea [biblioteca de plantillas de C++ (WRL) de Windows en tiempo de ejecución](wrl/windows-runtime-cpp-template-library-wrl.md).

## <a name="see-also"></a>Vea también

[C++ en Visual Studio](../overview/visual-cpp-in-visual-studio.md)<br/>
[Información general de la programación para Windows en C++](../windows/overview-of-windows-programming-in-cpp.md)<br/>