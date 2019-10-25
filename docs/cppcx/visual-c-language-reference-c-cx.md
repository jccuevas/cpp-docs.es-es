---
title: C++Referencia del lenguaje/CX
ms.date: 09/15/2017
ms.assetid: 3f6abf92-4e5e-4ed8-8e11-f9252380d30a
ms.openlocfilehash: ed8e2374daf862e99517fb113e869504b7c7aabc
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/06/2019
ms.locfileid: "70740865"
---
# <a name="ccx-language-reference"></a>C++Referencia del lenguaje/CX

C++/CX es un conjunto de extensiones para el C++ lenguaje que permiten la creación de aplicaciones de Windows y Windows Runtime componentes en una expresión que sea lo más cercana posible a C++la moderna. Use C++/CX para escribir aplicaciones y componentes de Windows en código nativo que interactúen C#fácilmente con visual, Visual Basic y JavaScript, y con otros lenguajes que admitan el Windows Runtime. En los casos excepcionales que requieren acceso directo a las interfaces COM sin procesar, o a código no excepcional, puede usar la [biblioteca C++ de plantillas de Windows Runtime (WRL)](../windows/windows-runtime-cpp-template-library-wrl.md).

> [!NOTE]
> **/WinRT es la alternativa recomendada a C++/CX. [ C++](/windows/uwp/cpp-and-winrt-apis/index)** Se trata de una nueva proyección de lenguaje C++ 17 estándar para Windows Runtime API, disponible en el último SDK de Windows 10 de la versión 1803 en adelante. C++/WinRT se implementa completamente en los archivos de encabezado y está diseñado para proporcionar acceso de primera clase a la API moderna de Windows.
>
> Con C++/WinRT, puede consumir y crear Windows Runtime API con cualquier compilador de c++ 17 compatible con los estándares. C++ / c++ / WinRT normalmente funciona mejor y genera archivos binarios más pequeños que ninguna otra opción de idioma para el tiempo de ejecución de Windows. Seguiremos admitiendo C++/CX y WRL, pero recomendamos encarecidamente que las nuevas aplicaciones usen C++/WinRT. Para obtener más información, consulte [C++/WinRT](/windows/uwp/cpp-and-winrt-apis/index).

Con C++/CX, puede crear:

- C++Plataforma universal de Windows (UWP) aplicaciones que usan XAML para definir la interfaz de usuario y usar la pila nativa. Para obtener más información, vea [crear una aplicación "Hello World" C++ en (UWP)](/windows/uwp/get-started/create-a-basic-windows-10-app-in-cpp).

- C++Windows Runtime componentes que pueden usar las aplicaciones de Windows basadas en JavaScript. Para obtener más información, consulta [Creating Windows Runtime Components in C++](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp).

- Aplicaciones con numerosos gráficos y juegos DirectX de Windows. Para obtener más información, consulte [crear un juego de UWP sencillo con DirectX](/windows/uwp/gaming/tutorial--create-your-first-uwp-directx-game).

## <a name="related-articles"></a>Artículos relacionados

|||
|-|-|
|[Referencia rápida](../cppcx/quick-reference-c-cx.md)|Tabla de palabras clave y operadores C++para/CX.|
|[Sistema de tipos](../cppcx/type-system-c-cx.md)|Describe los C++tipos y construcciones de programación básicos de/CX y cómo usar C++/CX para consumir y crear Windows Runtime tipos.|
|[Compilación de aplicaciones y bibliotecas](../cppcx/building-apps-and-libraries-c-cx.md)|Describe cómo usar el IDE para compilar aplicaciones y vincular a bibliotecas y dll estáticas.|
|[Interoperación con otros lenguajes](../cppcx/interoperating-with-other-languages-c-cx.md)|Describe cómo se pueden usar los componentes que se C++escriben con/CX con componentes escritos en JavaScript, cualquier lenguaje administrado o la biblioteca de plantillas de C++ Windows Runtime.|
|[Subprocesamiento y serialización](../cppcx/threading-and-marshaling-c-cx.md)|Describe cómo especificar el comportamiento de subprocesamiento y cálculo de referencias de los componentes que crees.|
|[Referencia de espacios de nombres](../cppcx/namespaces-reference-c-cx.md)|Hace referencia a documentación para el espacio de nombres predeterminado, el espacio de nombres Platform, Platform::Collections y los espacios de nombres relacionados.|
|[Funciones de CRT no admitidas en aplicaciones de la Plataforma universal de Windows](../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)|Enumera las funciones de CRT que no se pueden usar en aplicaciones de Windows Runtime.|
|[Introducción a las aplicaciones de Windows 10](/windows/uwp/get-started/)|Proporcionan orientación de alto nivel sobre las aplicaciones de Windows 10 y vínculos a más información.|
|[C++/CX, parte 0 \[de\]n: Una introducción](https://blogs.msdn.microsoft.com/vcblog/2012/08/29/ccx-part-0-of-n-an-introduction/)<br /><br />[C++/CX, parte 1 \[de\]n: Una clase simple](https://blogs.msdn.microsoft.com/vcblog/2012/09/05/ccx-part-1-of-n-a-simple-class/)<br /><br />[C++/CX, parte 2 \[de\]n: Tipos que desgasten los sombreros](https://blogs.msdn.microsoft.com/vcblog/2012/09/17/ccx-part-2-of-n-types-that-wear-hats/)<br /><br />[C++/CX, parte 3 \[de\]n: En construcción](https://blogs.msdn.microsoft.com/vcblog/2012/10/05/ccx-part-3-of-n-under-construction/)<br /><br />[C++/CX, parte 4 \[de\]n: Funciones miembro estáticas](https://blogs.msdn.microsoft.com/vcblog/2012/10/19/ccx-part-4-of-n-static-member-functions/)|Una serie de blog introductorio C++en/CX.|
