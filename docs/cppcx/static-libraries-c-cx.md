---
title: Bibliotecas estáticas (C++/CX)
ms.date: 02/03/2017
ms.assetid: 7faf53c8-fa21-42cc-8246-d32533ef9dfa
ms.openlocfilehash: 188ba06518bf6cdd154b7d6bd61216ed1e4ffad3
ms.sourcegitcommit: 18d3b1e9cdb4fc3a76f7a650c31994bdbd2bde64
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/29/2019
ms.locfileid: "64877241"
---
# <a name="static-libraries-ccx"></a>Bibliotecas estáticas (C++/CX)

Una biblioteca estática que se usa en una aplicación de plataforma Universal de Windows (UWP) puede contener código de la norma ISO C++, incluidos los tipos STL y también las llamadas a API de Win32 que no se excluyen de la plataforma de aplicaciones de Windows en tiempo de ejecución. Una biblioteca estática utiliza componentes de Windows en tiempo de ejecución y puede crear componentes de Windows en tiempo de ejecución con ciertas restricciones.

## <a name="creating-static-libraries"></a>Crear bibliotecas estáticas


Instrucciones para crear un nuevo proyecto varían dependiendo de qué versión de Visual Studio instalado. Asegúrese de que tiene el selector de versión en la esquina superior izquierda se establece en la versión correcta.

::: moniker range="vs-2019"

### <a name="to-create-a-uwp-static-library-in-visual-studio-2019"></a>Para crear una biblioteca estática de UWP en Visual Studio de 2019

1. En la barra de menús, elija **archivo** > **New** > **proyecto** para abrir el **crear un nuevo proyecto** cuadro de diálogo.

1. En la parte superior del cuadro de diálogo, establezca **lenguaje** a **C++**, establezca **plataforma** a **Windows**y establezca **deltipodeproyecto** a **UWP**. 

1. En la lista filtrada de tipos de proyecto, elija **biblioteca estática (Windows Universal - C++/CX)** , a continuación, elija **siguiente**. En la siguiente página, asigne un nombre al proyecto y, si lo desea, especifique la ubicación del proyecto.

1. Elija la **crear** botón para crear el proyecto.

::: moniker-end

::: moniker range="<=vs-2017"

### <a name="to-create-a-uwp-static-library-in-visual-studio-2017-or-visual-studio-2015"></a>Para crear una biblioteca estática de UWP en Visual Studio 2017 o Visual Studio 2015

1. En la barra de menús, elija **Archivo** > **Nuevo** > **Proyecto**. En **Visual C++** > **Windows Universal** elija **biblioteca estática (Windows Universal)**.

1. En el **Explorador de soluciones**, abra el menú contextual del proyecto y, a continuación, elija **Propiedades**. En el **propiedades** cuadro de diálogo el **propiedades de configuración** > **C o C++** , establezca **usar Windows en tiempo de ejecución extensión** a **Sí (/ZW)**.

::: moniker-end

Cuando se compila una nueva biblioteca estática, si realiza una llamada a una API de Win32 excluida para las aplicaciones para UWP, el compilador producirá el error C3861, "No se encontró el identificador". Para buscar un método alternativo que es compatible con el tiempo de ejecución de Windows, consulte [alternativas a las API de Windows en aplicaciones para UWP](/uwp/win32-and-com/alternatives-to-windows-apis-uwp).

Si agrega un proyecto de biblioteca estática de C++ a una solución de aplicación para UWP, es posible que deba actualizar los valores de las propiedades del proyecto de biblioteca para que se establece la propiedad de soporte técnico UWP en **Sí**. Sin esta configuración, el código se compila y vínculos, pero un error que se produce cuando se intenta comprobar la aplicación para la Microsoft Store. La biblioteca estática se debe compilar con la misma configuración del compilador que el proyecto que la utiliza.

Si utilizas una biblioteca estática que crea clases `ref` públicas, clases de interfaz públicas o clases de valor públicas, el vinculador produce esta advertencia:

> **warning LNK4264:** almacenamiento de un archivo objeto compilado con /ZW en una biblioteca estática; tenga en cuenta que, al crear tipos en tiempo de ejecución de Windows no se recomienda para vincular con una biblioteca estática que contiene los metadatos de Windows en tiempo de ejecución.

Puede ignorar la advertencia solo si la biblioteca estática no está generando los componentes de Windows en tiempo de ejecución que se utilizan fuera de la propia biblioteca. Si la biblioteca no utiliza un componente que define, el vinculador puede optimizar correctamente la implementación aunque los metadatos públicos contengan la información de tipo. Esto significa que los componentes públicos de una biblioteca estática se compilarán pero no se activarán en tiempo de ejecución. Por este motivo, se debe implementar cualquier componente de Windows en tiempo de ejecución que está pensado para su uso por otros componentes o aplicaciones en una biblioteca de vínculos dinámicos (DLL).

## <a name="see-also"></a>Vea también

[Subprocesamiento y serialización](../cppcx/threading-and-marshaling-c-cx.md)
