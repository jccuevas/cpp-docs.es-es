---
title: Bibliotecas estáticas (C++/CX)
ms.date: 02/03/2017
ms.assetid: 7faf53c8-fa21-42cc-8246-d32533ef9dfa
ms.openlocfilehash: 3c4bfd28b805903a2e596ef6d648ff31b0b8261c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81358109"
---
# <a name="static-libraries-ccx"></a>Bibliotecas estáticas (C++/CX)

Una biblioteca estática que se usa en una aplicación de la Plataforma universal de Windows (UWP) puede contener código C++ estándar ISO, incluidos los tipos STL, y también llamadas a las API de Win32 que no están excluidas de la plataforma de aplicaciones de Windows en tiempo de ejecución. Una biblioteca estática consume componentes de Windows Runtime y puede crear componentes de Windows Runtime con ciertas restricciones.

## <a name="creating-static-libraries"></a>Crear bibliotecas estáticas

Las instrucciones para crear un nuevo proyecto varían en función de la versión de Visual Studio que haya instalado. Para ver la documentación de su versión preferida de Visual Studio, use el control Selector de **versiones.** Se encuentra en la parte superior de la tabla de contenido de esta página.

::: moniker range="vs-2019"

### <a name="to-create-a-uwp-static-library-in-visual-studio-2019"></a>Para crear una biblioteca estática para UWP en Visual Studio 2019

1. En la barra de menús, seleccione **Archivo** > **Nuevo** > **Proyecto** para abrir el cuadro de diálogo **Crear nuevo proyecto**.

1. En la parte superior del cuadro de diálogo, establezca **Idioma** en **C++,** Establezca **Plataforma** en **Windows**y Tipo de **proyecto** en **UWP**.

1. En la lista filtrada de tipos de proyecto, elija **Biblioteca estática (Windows universal - C++/CX) y,** a continuación, elija **Siguiente**. En la página siguiente, asigne un nombre al proyecto y especifique la ubicación del proyecto si lo desea.

1. Elija el botón **Crear** para crear el proyecto.

::: moniker-end

::: moniker range="<=vs-2017"

### <a name="to-create-a-uwp-static-library-in-visual-studio-2017-or-visual-studio-2015"></a>Para crear una biblioteca estática para UWP en Visual Studio 2017 o Visual Studio 2015

1. En la barra de menús, elija **Archivo** > **nuevo** > **proyecto**. En **Visual C++** > **Windows Universal,** elija Biblioteca estática **(Windows universal).**

1. En el **Explorador**de soluciones , abra el menú contextual del proyecto y, a continuación, elija **Propiedades**. En el cuadro de diálogo **Propiedades,** en la página **Propiedades** > de configuración**C/C++,** establezca Consumir extensión de **Windows en tiempo** de ejecución en **Sí (/ZW)**.

::: moniker-end

Al compilar una nueva biblioteca estática, si realiza una llamada a una API de Win32 que se excluye para aplicaciones para UWP, el compilador generará el error C3861, "Identificador no encontrado." Para buscar un método alternativo compatible con Windows Runtime, consulta [Alternativas a las API](/uwp/win32-and-com/alternatives-to-windows-apis-uwp)de Windows en aplicaciones para UWP .

Si agregas un proyecto de biblioteca estática de C++ a una solución de aplicación para UWP, es posible que tengas que actualizar la configuración de propiedades del proyecto de biblioteca para que la propiedad de compatibilidad con UWP esté establecida en **Sí**. Sin esta configuración, el código se compila y vincula, pero se produce un error al intentar comprobar la aplicación para Microsoft Store. La biblioteca estática se debe compilar con la misma configuración del compilador que el proyecto que la utiliza.

Si utilizas una biblioteca estática que crea clases `ref` públicas, clases de interfaz públicas o clases de valor públicas, el vinculador produce esta advertencia:

> **Advertencia LNK4264:** archivo de objeto de archivado compilado con /ZW en una biblioteca estática; Tenga en cuenta que al crear tipos de Windows Runtime no se recomienda vincular con una biblioteca estática que contiene metadatos de Windows Runtime.

Puede omitir la advertencia de forma segura solo si la biblioteca estática no está produciendo componentes de Windows Runtime que se consumen fuera de la propia biblioteca. Si la biblioteca no utiliza un componente que define, el vinculador puede optimizar correctamente la implementación aunque los metadatos públicos contengan la información de tipo. Esto significa que los componentes públicos de una biblioteca estática se compilarán pero no se activarán en tiempo de ejecución. Por este motivo, cualquier componente de Windows Runtime destinado al consumo por otros componentes o aplicaciones debe implementarse en una biblioteca de vínculos dinámicos (DLL).

## <a name="see-also"></a>Consulte también

[Subprocesamiento y serialización](../cppcx/threading-and-marshaling-c-cx.md)
