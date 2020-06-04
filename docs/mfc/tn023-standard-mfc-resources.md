---
title: 'TN023: Recursos de MFC estándar'
ms.date: 11/04/2016
helpviewer_keywords:
- resources [MFC]
- TN023
- standard resources
ms.assetid: 60af8415-c576-4c2f-a711-ca5da0b9a1f2
ms.openlocfilehash: 90e7b9b7c354ba919c3dee279725b4498bea57ff
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370379"
---
# <a name="tn023-standard-mfc-resources"></a>TN023: Recursos de MFC estándar

Esta nota describe los recursos estándar proporcionados y necesarios por la biblioteca MFC.

## <a name="standard-resources"></a>Recursos estándar

MFC ofrece dos categorías de recursos predefinidos que puede usar en la aplicación: recursos de imágenes prediseñadas y recursos de marco estándar.

Los recursos de imágenes prediseñadas son recursos adicionales de los que el marco de trabajo no depende, pero que es posible que desee agregar a la interfaz de usuario de la aplicación. Los siguientes recursos de imágenes prediseñadas se encuentran en el ejemplo general de MFC [CLIPART:](../overview/visual-cpp-samples.md)

- Common.rc: Un único archivo de recursos que contiene:

  - Una gran colección de iconos que representan una variedad de tareas empresariales y de procesamiento de datos.

  - Varios cursores comunes (véase también Afxres.rc).

  - Un mapa de bits de barra de herramientas que contiene varios botones de barra de herramientas.

  - El mapa de bits y los recursos de icono que usa Commdlg.dll.

- Indicate.rc: contiene recursos de cadena para los indicadores de estado de clave de la barra de estado, como "CAP" para Bloq Mayús.

- Prompts.rc: contiene recursos de cadena de solicitud de menú para cada comando predefinido, como "Crear un nuevo documento" para ID_FILE_NEW.

- Commdlg.rc: un archivo .rc compatible con Visual C++ que contiene las plantillas de diálogo COMMDLG estándar.

Los recursos de marco estándar son recursos con ID definidos por AFX de los que depende el marco de trabajo para las implementaciones internas. Rara vez tendrá que cambiar estos recursos definidos por AFX. Si lo hace, debe seguir el procedimiento descrito más adelante en este tema.

Los siguientes recursos de marco de trabajo se encuentran en el directorio MFC-INCLUDE:

- Afxres.rc: recursos comunes utilizados por el marco de trabajo.

- Afxprint.rc: Recursos específicos para la impresión.

- Afxolecl.rc: recursos específicos de las aplicaciones cliente OLE.

- Afxolev.rc: recursos específicos para aplicaciones de servidor OLE completas.

## <a name="using-clip-art-resources"></a>Uso de recursos Clip-Art

#### <a name="to-use-a-clip-art-binary-resource"></a>Para utilizar un recurso binario de imágenes prediseñadas

1. Abra el archivo de recursos de la aplicación en Visual C++.

1. Abra Common.rc. Este archivo contiene todos los recursos binarios de imágenes prediseñadas. Esto puede tardar algún tiempo porque se compila el archivo Common.rc.

1. Mantenga presionada la tecla CTRL mientras arrastra los recursos que desea usar desde Common.rc al archivo de recursos de la aplicación.

Para utilizar otros recursos de imágenes prediseñadas, siga los mismos pasos. La única diferencia es que abrirá el archivo .rc adecuado en lugar de Common.rc.

> [!NOTE]
> Tenga cuidado de no mover involuntariamente los recursos fuera de Common.rc permanentemente. Si mantiene presionada la tecla CTRL mientras arrastra recursos, creará una copia. Si no mantiene presionada la tecla CTRL mientras arrastra, los recursos se moverán. Si le preocupa que haya realizado cambios accidentalmente en el archivo Common.rc, haga clic en "No" cuando se le pregunte si desea guardar los cambios en Common.rc.

> [!NOTE]
> Los archivos de recursos .rc tienen un recurso TEXTINCLUDE especial que le impedirá guardar accidentalmente encima de los archivos .rc estándar.

### <a name="customizing-standard-framework-resources"></a>Personalización de los recursos marco estándar

Los recursos de marco estándar normalmente se incluyen en una aplicación mediante el comando #include en el archivo de recursos de una aplicación. AppWizard generará un archivo de recursos. Este archivo incluye los recursos de marco estándar adecuados, en función de las opciones de AppWizard que seleccione. Puede revisar, agregar o quitar qué recursos se incluyen cambiando las directivas en tiempo de compilación. Para ello, abra el menú **Recurso** y seleccione **Establecer incluye**. Consulte el elemento de edición "Directivas de tiempo de compilación". Por ejemplo:

```
#include "afxres.rc"
#include "afxprint.rc"
```

El caso más común de personalizar los recursos de marco estándar es agregar o quitar incluir adicionales para la impresión, cliente OLE y compatibilidad con el servidor OLE.

En algunos casos raros, es posible que desee personalizar el contenido de los recursos de marco estándar para la aplicación en particular, no solo agregar y quitar todo el archivo. Los pasos siguientes muestran cómo puede limitar los recursos que se incluyen:

##### <a name="to-customize-the-contents-of-a-standard-resource-file"></a>Para personalizar el contenido de un archivo de recursos estándar

1. Abra el archivo de recursos en Visual C++.

1. Mediante el comando Incluye conjunto `#include` de recursos, quite el archivo .rc estándar que desea personalizar. Por ejemplo, para personalizar la barra `#include "afxprint.rc"` de herramientas de vista previa de impresión, quite la línea.

1. Abra los archivos de recursos estándar adecuados en MFC-INCLUDE. Siguiendo el ejemplo anterior en este tema, el archivo adecuado es MFC-Include-Aafxprint.rc

1. Copie todos los recursos del archivo .rc estándar en el archivo de recursos de la aplicación.

1. Modifique la copia de los recursos estándar en el archivo de recursos de la aplicación.

> [!NOTE]
> No modifique los recursos directamente en los archivos .rc estándar. Si lo hace, modificará los recursos disponibles en cada aplicación, no solo en la que está trabajando actualmente.

## <a name="see-also"></a>Consulte también

[Notas técnicas por número](../mfc/technical-notes-by-number.md)<br/>
[Notas técnicas por categoría](../mfc/technical-notes-by-category.md)
