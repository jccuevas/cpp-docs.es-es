---
title: Actualizar proyectos desde versiones anteriores de Visual C++
ms.date: 11/04/2016
helpviewer_keywords:
- 32-bit code porting
- upgrading Visual C++ applications, 32-bit code
ms.assetid: 18cdacaa-4742-43db-9e4c-2d9e73d8cc84
ms.openlocfilehash: dcbec57c75b4dc6fb72a3b35040e12cab0e7111e
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/11/2019
ms.locfileid: "57740877"
---
# <a name="upgrading-projects-from-earlier-versions-of-visual-c"></a>Actualizar proyectos desde versiones anteriores de Visual C++

En la mayoría de los casos, es posible abrir un proyecto creado en una versión anterior de Visual Studio. Sin embargo, para ello, Visual Studio actualiza el proyecto. Si se guarda este proyecto actualizado, no se puede abrir en la versión anterior.

> [!IMPORTANT]
> Si se intenta convertir un proyecto que ya se convirtió, Visual Studio pide confirmación porque la reconversión elimina archivos existentes.

Muchos proyectos y soluciones actualizados se pueden compilar correctamente sin realizar modificaciones. Sin embargo, en algunos proyectos puede ser necesario realizar cambios en la configuración, el código fuente o ambos. Se recomienda usar las instrucciones siguientes para solucionar primero los problemas de configuración y, a continuación, si el proyecto no se compila, solucionar los problemas de código. Para obtener más información, vea [Información general sobre posibles problemas de actualización](../porting/overview-of-potential-upgrade-issues-visual-cpp.md).

1. Haga una copia de los archivos de proyecto y de solución existentes. Instale la versión actual de Visual Studio y la versión anterior en paralelo para poder comparar las versiones de los archivos si lo desea.

2. En la versión actual de Visual Studio, abra (y por tanto actualice) la copia del proyecto o la solución y guárdela.

3. Para cada proyecto convertido, abra el menú contextual y elija **Propiedades**. En **Propiedades de configuración**, seleccione **General** y después, en **Conjunto de herramientas de la plataforma**, seleccione la versión actual. (Por ejemplo, para Visual Studio 2017, seleccione **v141**).

4. Compile la solución. Si se produce un error en la compilación, modifique los valores y recompile.

Los orígenes de datos están en un proyecto de base de datos independiente de forma que pueda modificar y depurar más fácilmente los procedimientos almacenados en esos orígenes. Si actualiza un proyecto de C++ que contiene orígenes de datos, se crea automáticamente un proyecto de base de datos independiente.

Para obtener información sobre cómo actualizar las versiones de Windows de destino, consulte [Modificar WINVER y _WIN32_WINNT](../porting/modifying-winver-and-win32-winnt.md).

## <a name="see-also"></a>Vea también

[Cambios del sistema de compilación](../build/build-system-changes.md)<br/>
[Novedades de Visual C++ en Visual Studio 2017](../what-s-new-for-visual-cpp-in-visual-studio.md)<br/>
[Historial de cambios en Visual C++ 2003-2015](../porting/visual-cpp-change-history-2003-2015.md)<br/>
[Comportamiento no estándar](../cpp/nonstandard-behavior.md)
