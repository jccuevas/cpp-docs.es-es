---
title: Procedimiento Integrar herramientas personalizadas en las propiedades del proyecto
ms.date: 05/16/2019
helpviewer_keywords:
- 'msbuild (c++), howto: integrate custom tools'
ms.assetid: f32d91a4-44e9-4de3-aa9a-1c7f709ad2ee
ms.openlocfilehash: 0c0233ad6715a3adb7d47f021a87207f288d5139
ms.sourcegitcommit: a10c9390413978d36b8096b684d5ed4cf1553bc8
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/17/2019
ms.locfileid: "65837031"
---
# <a name="how-to-integrate-custom-tools-into-the-project-properties"></a>Procedimiento Integrar herramientas personalizadas en las propiedades del proyecto

Puede agregar opciones de herramienta personalizadas a la ventana **Páginas de propiedades** de Visual Studio mediante la creación de un archivo de esquema XML subyacente.

La sección **Propiedades de configuración** de la ventana **Páginas de propiedades** muestra los grupos de configuración que se conocen como *reglas*. Cada regla contiene la configuración de una herramienta o un grupo de características. Por ejemplo, la regla **Enlazador** contiene la configuración de la herramienta del enlazador. La configuración de una regla se puede subdividir en *categorías*.

En este documento se explica cómo crear un archivo en un directorio establecido que contiene propiedades de la herramienta personalizada para que las propiedades se carguen cuando se inicie Visual Studio. Para más información sobre cómo modificar el archivo, vea [Extensibilidad de la plataforma Parte 2](https://blogs.msdn.microsoft.com/vsproject/2009/06/18/platform-extensibility-part-2/) en el blog del equipo de proyecto de Visual Studio.

### <a name="to-add-or-change-project-properties"></a>Para agregar o cambiar las propiedades del proyecto

1. En el editor XML, cree un archivo XML.

1. Guarde el archivo en la carpeta `VCTargets\1033` de Visual Studio. Tendrá una ruta de acceso diferente para cada idioma y cada edición de Visual Studio que esté instalada. Por ejemplo, la ruta predeterminada a la carpeta para Visual Studio Community de 2019 en inglés es `C:\Program Files (x86)\Microsoft Visual Studio\2019\Community\Common7\IDE\VC\VCTargets`. Ajuste la ruta de acceso para el idioma y la edición de Visual Studio. Cada regla de la página **Páginas de propiedades** se representa mediante un archivo XML en esta carpeta. Asegúrese de que el archivo tiene un nombre único en la carpeta.

1. Copie el contenido de `%ProgramFiles%\Microsoft Visual Studio\2019\<VS Edition>\Common7\IDE\VC\VCTargets\<LCID>\cl.xml` (o la ruta de acceso que tenga), ciérrelo sin guardar los cambios y, después, pegue el contenido en el nuevo archivo XML. Puede usar cualquier archivo de esquema XML: este es simplemente uno que puede usarse para que empiece con una plantilla.

1. En el nuevo archivo XML, modifique el contenido según sus requisitos. No olvide cambiar los valores de **Nombre de la regla** y **Rule.DisplayName** en la parte superior del archivo.

1. Guarde los cambios y cierre el archivo.

1. Los archivos XML de `%ProgramFiles%\Microsoft Visual Studio\2019\<VS Edition>\Common7\IDE\VC\VCTargets\<LCID>` (o la ubicación donde los guardó) se cargan cuando se inicia Visual Studio. Por lo tanto, para probar el nuevo archivo, debe reiniciar Visual Studio.

1. En el **Explorador de soluciones**, haga clic con el botón derecho en un proyecto y después seleccione **Propiedades**. En la ventana **Páginas de propiedades**, en el panel izquierdo, compruebe que hay un nuevo nodo con el nombre de la regla.

## <a name="see-also"></a>Vea también

[MSBuild en la línea de comandos - C++](msbuild-visual-cpp.md)
