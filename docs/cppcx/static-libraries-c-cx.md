---
title: Bibliotecas estáticas (C++/CX)
ms.date: 02/03/2017
ms.assetid: 7faf53c8-fa21-42cc-8246-d32533ef9dfa
ms.openlocfilehash: 42c247650f778dcc9dbfa13d27cbb0244c0ebbc2
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "80077977"
---
# <a name="static-libraries-ccx"></a>Bibliotecas estáticas (C++/CX)

Una biblioteca estática que se usa en una aplicación Plataforma universal de Windows (UWP) puede contener código ISO estándar C++ , incluidos los tipos STL, y también llama a las API de Win32 que no se excluyen de la plataforma de aplicaciones Windows Runtime. Una biblioteca estática consume Windows Runtime componentes de y puede crear componentes de Windows Runtime con ciertas restricciones.

## <a name="creating-static-libraries"></a>Crear bibliotecas estáticas

Las instrucciones para crear un nuevo proyecto varían en función de la versión de Visual Studio que tenga instalada. Asegúrese de que tiene el selector de versión en la parte superior izquierda establecido en la versión correcta.

::: moniker range="vs-2019"

### <a name="to-create-a-uwp-static-library-in-visual-studio-2019"></a>Para crear una biblioteca estática de UWP en Visual Studio 2019

1. En la barra de menús, elija **archivo** > **nuevo** > **proyecto** para abrir el cuadro de diálogo **crear un nuevo proyecto** .

1. En la parte superior del cuadro de diálogo **Language** , establezca **C++** Language en, establezca **plataforma** en **Windows**y establezca **tipo de proyecto** en **UWP**.

1. En la lista filtrada de tipos de proyecto, elija **biblioteca estática (universal Windows C++-/CX)** y, a continuación, elija **siguiente**. En la página siguiente, asigne un nombre al proyecto y especifique la ubicación del proyecto si lo desea.

1. Elija el botón **Crear** para crear el proyecto.

::: moniker-end

::: moniker range="<=vs-2017"

### <a name="to-create-a-uwp-static-library-in-visual-studio-2017-or-visual-studio-2015"></a>Para crear una biblioteca estática de UWP en Visual Studio 2017 o Visual Studio 2015

1. En la barra de menús, elija **Archivo** > **Nuevo** > **Proyecto**. En **Visual C++**  > **Windows universal** elija **biblioteca estática (Windows universal)** .

1. En el **Explorador de soluciones**, abra el menú contextual del proyecto y, a continuación, elija **Propiedades**. En el cuadro de diálogo **propiedades** , en la página **propiedades de configuración** > **C/C++**  , establezca **consumir Windows Runtime extensión** en **sí (/ZW)** .

::: moniker-end

Al compilar una nueva biblioteca estática, si realiza una llamada a una API de Win32 excluida para las aplicaciones UWP, el compilador generará el error C3861, "no se encuentra el identificador". Para buscar un método alternativo compatible con el Windows Runtime, consulte [alternativas a las API de Windows en aplicaciones para UWP](/uwp/win32-and-com/alternatives-to-windows-apis-uwp).

Si agrega un C++ proyecto de biblioteca estática a una solución de aplicación para UWP, es posible que tenga que actualizar los valores de propiedad del proyecto de biblioteca para que la propiedad compatibilidad de UWP esté establecida en **sí**. Sin esta configuración, el código compila y vincula, pero se produce un error al intentar comprobar la aplicación para el Microsoft Store. La biblioteca estática se debe compilar con la misma configuración del compilador que el proyecto que la utiliza.

Si utilizas una biblioteca estática que crea clases `ref` públicas, clases de interfaz públicas o clases de valor públicas, el vinculador produce esta advertencia:

> **ADVERTENCIA LNK4264:** archivo objeto de archivo compilado con/ZW en una biblioteca estática; Tenga en cuenta que al crear tipos de Windows Runtime, no se recomienda vincular con una biblioteca estática que contenga metadatos de Windows Runtime.

Puede omitir la advertencia sin ningún problema solo si la biblioteca estática no está generando Windows Runtime componentes consumidos fuera de la propia biblioteca. Si la biblioteca no utiliza un componente que define, el vinculador puede optimizar correctamente la implementación aunque los metadatos públicos contengan la información de tipo. Esto significa que los componentes públicos de una biblioteca estática se compilarán pero no se activarán en tiempo de ejecución. Por esta razón, todos los componentes de Windows Runtime que están destinados a ser consumidos por otros componentes o aplicaciones deben implementarse en una biblioteca de vínculos dinámicos (DLL).

## <a name="see-also"></a>Consulte también

[Subprocesamiento y serialización](../cppcx/threading-and-marshaling-c-cx.md)
