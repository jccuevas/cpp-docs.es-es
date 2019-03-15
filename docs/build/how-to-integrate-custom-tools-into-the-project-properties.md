---
title: Filtrar Integrar herramientas personalizadas en las propiedades del proyecto
ms.date: 04/27/2016
f1_keywords:
- msbuild.cpp.howto.integratecustomtools
helpviewer_keywords:
- 'msbuild (c++), howto: integrate custom tools'
ms.assetid: f32d91a4-44e9-4de3-aa9a-1c7f709ad2ee
ms.openlocfilehash: a959eddb36a2de90ebd5b5b1b9eb5e2f4e67c03a
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "57810164"
---
# <a name="how-to-integrate-custom-tools-into-the-project-properties"></a>Filtrar Integrar herramientas personalizadas en las propiedades del proyecto

Puede agregar opciones de herramienta personalizada de Visual Studio **páginas de propiedades** ventana mediante la creación de un archivo de esquema XML subyacente.

El **propiedades de configuración** sección de la **páginas de propiedades** ventana muestra los grupos de configuración que se conocen como *reglas*. Cada regla contiene la configuración de una herramienta o un grupo de funciones. Por ejemplo, el **vinculador** regla contiene la configuración de la herramienta del vinculador. La configuración de una regla se puede subdividir en *categorías*.

Este documento explica cómo crear un archivo en un directorio de conjunto que contiene las propiedades de la herramienta personalizada para que las propiedades se cargan cuando se inicia Visual Studio. Para obtener información acerca de cómo modificar el archivo, consulte [plataforma Extensibilty 2ª](https://blogs.msdn.microsoft.com/vsproject/2009/06/18/platform-extensibility-part-2/) en el blog del equipo de proyecto de Visual Studio.

### <a name="to-add-or-change-project-properties"></a>Para agregar o cambiar las propiedades del proyecto

1. En el editor XML, cree un archivo XML.

1. Guarde el archivo en Visual Studio 2017 `VCTargets\1033` carpeta. Tendrá una ruta de acceso diferente para cada idioma y de cada edición de Visual Studio 2017 instalado. Por ejemplo, es la ruta de acceso de carpeta en la edición de Visual Studio Enterprise de inglés `%ProgramFiles%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\VC\VCTargets\1033`. Ajuste la ruta de acceso para su idioma y la edición de Visual Studio. Cada regla en el **páginas de propiedades** ventana se representa mediante un archivo XML en esta carpeta. Asegúrese de que el archivo se nombra en la carpeta.

1. Copie el contenido de `%ProgramFiles%\Microsoft Visual Studio\2017\<VS Edition>\Common7\IDE\VC\VCTargets\<LCID>\cl.xml`, cerrarlo sin guardar los cambios y, a continuación, pegue el contenido en el nuevo archivo XML. Puede usar cualquier archivo de esquema XML: esta es solo una puede usarse para que empezar con una plantilla.

1. En el nuevo archivo XML, modificar el contenido según sus requisitos. No olvide cambiar el **nombre de la regla** y **Rule.DisplayName** en la parte superior del archivo.

1. Guarde los cambios y cierre el archivo.

1. Archivos XML en `%ProgramFiles%\Microsoft Visual Studio\2017\<VS Edition>\Common7\IDE\VC\VCTargets\<LCID>` se cargan cuando se inicia Visual Studio. Por lo tanto, para probar el nuevo archivo, reinicie Visual Studio.

1. En **el Explorador de soluciones**, haga clic en un proyecto y, a continuación, haga clic en **propiedades**. En el **páginas de propiedades** ventana, en el panel izquierdo, compruebe que hay un nuevo nodo con el nombre de la regla.

## <a name="see-also"></a>Vea también

[MSBuild en la línea de comandos - C++](msbuild-visual-cpp.md)
