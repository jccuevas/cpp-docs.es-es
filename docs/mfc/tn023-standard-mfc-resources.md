---
title: 'TN023: Recursos de MFC estándar'
ms.date: 11/04/2016
f1_keywords:
- vc.mfc.resources
helpviewer_keywords:
- resources [MFC]
- TN023
- standard resources
ms.assetid: 60af8415-c576-4c2f-a711-ca5da0b9a1f2
ms.openlocfilehash: b4edc00f77152b8d677f3113e0ed6386569b0988
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57277685"
---
# <a name="tn023-standard-mfc-resources"></a>TN023: Recursos de MFC estándar

Esta nota describe los recursos estándar proporcionada con y es necesario por la biblioteca MFC.

## <a name="standard-resources"></a>Recursos estándar

MFC proporciona dos categorías de recursos predefinidos que puede usar en la aplicación: recursos de imágenes prediseñadas y recursos de marco estándar.

Los recursos de imágenes prediseñadas son recursos adicionales que no dependen de la plataforma, pero que desea agregar a la interfaz de usuario de la aplicación. Los siguientes recursos de imagen prediseñada contenidos en el ejemplo General de MFC [CLIPART](../visual-cpp-samples.md):

- Common.rc: Un único archivo de recursos que contiene:

   - Una gran colección de iconos que representan una variedad de tareas de procesamiento de datos y de trabajo.

   - Varios cursores comunes (Vea también Afxres.rc).

   - Un mapa de bits de barra de herramientas que contiene varios botones de barra de herramientas.

   - Los recursos de mapa de bits y el icono que se usan por Commdlg.dll.

- Indicate.rc: Contiene recursos de cadena para los indicadores de estado de la tecla barra de estado, como "Límite" para BLOQ MAYÚS.

- Prompts.rc: Contiene recursos de cadena de mensaje de menú para cada comando predefinido, como "Crear un nuevo documento" para ID_FILE_NEW.

- Commdlg.rc: Un archivo .rc compatible de Visual C++ que contiene las plantillas de cuadro de diálogo COMMDLG estándar.

Recursos de marco estándar son con identificadores definidos por AFX que el marco de trabajo depende de las implementaciones internas. Rara vez necesitará cambiar estos recursos definidos en AFX. Si lo hace, debe seguir el procedimiento descrito más adelante en este tema.

Los siguientes recursos de marco de trabajo se incluyen en el directorio MFC\INCLUDE:

- Afxres.rc: Recursos comunes utilizados por el marco de trabajo.

- Afxprint.rc: Recursos específicos de impresión.

- Afxolecl.rc: Recursos específicos de las aplicaciones de cliente OLE.

- Afxolev.rc: Recursos específicos de aplicaciones de servidor completas OLE.

## <a name="using-clip-art-resources"></a>Uso de recursos de imagen prediseñada

#### <a name="to-use-a-clip-art-binary-resource"></a>Para usar un recurso binario imágenes prediseñadas

1. Abra el archivo de recursos de la aplicación en Visual C++.

1. Abra Common.rc. Este archivo contiene todos los recursos de imágenes binarias. Esto puede tardar algún tiempo porque el archivo Common.rc está compilado.

1. Mantenga presionada la tecla CTRL mientras arrastra los recursos que desea usar desde Common.rc al archivo de recursos de la aplicación.

Para usar otros recursos de imágenes prediseñadas, siga los mismos pasos. La única diferencia es que se abrirá el archivo .rc adecuado en lugar de Common.rc.

> [!NOTE]
>  Tenga cuidado de no mover accidentalmente los recursos fuera de Common.rc permanentemente. Si mantiene presionada la tecla CTRL mientras arrastra los recursos, se creará una copia. Si no presionado CTRL mientras arrastra, se moverá los recursos. Si le preocupa que podrían accidentalmente realizados los cambios en el archivo Common.rc, haga clic en "No" cuando se le pregunte si desea guardar los cambios en Common.rc.

> [!NOTE]
>  Los archivos de recursos de .rc contienen un recurso TEXTINCLUDE especial que no podrá guardar accidentalmente encima de los archivos .rc estándar.

### <a name="customizing-standard-framework-resources"></a>Personalización de los recursos de marco estándar

Recursos de marco estándar normalmente se incluyen en una aplicación utilizando el #include comando en el archivo de recursos de la aplicación. AppWizard generará un archivo de recursos. Este archivo incluye los recursos de marco estándar adecuado, según las opciones del Asistente para aplicaciones que seleccione. Puede revisar, agregar o quitar los recursos que se incluyen al cambiar las directivas de tiempo de compilación. Para ello, abra el **recursos** menú y seleccione **inclusión**. Vistazo a "Directivas de tiempo de compilación" Editar elemento. Por ejemplo:

```
#include "afxres.rc"
#include "afxprint.rc"
```

El caso más común de personalización de los recursos de marco estándar consiste en Agregar o quitar adicionales se incluye para la impresión, OLE cliente y soporte técnico de servidor OLE.

En algunos casos excepcionales que desea personalizar el contenido de los recursos de marco estándar para su aplicación particular, no solo agregar y quitar todo el archivo. Los siguientes pasos muestran cómo puede limitar los recursos que se incluyen:

##### <a name="to-customize-the-contents-of-a-standard-resource-file"></a>Para personalizar el contenido de un archivo de recursos estándar

1. Abra el archivo de recursos en Visual C++.

1. El comando de inclusión de recursos establecidos, quitar el `#include` para el archivo .rc estándar que desea personalizar. Por ejemplo, para personalizar la barra de herramientas de vista previa de impresión, quite el `#include "afxprint.rc"` línea.

1. Abra los archivos de recursos estándar adecuado en MFC\INCLUDE. Siguiendo el ejemplo anteriormente en este tema, el archivo adecuado es MFC\Include\Aafxprint.rc

1. Copie todos los recursos del archivo .rc estándar al archivo de recursos de la aplicación.

1. Modificar la copia de los recursos estándar en el archivo de recursos de la aplicación.

> [!NOTE]
>  No modifique los recursos directamente en los archivos .rc estándar. Si lo hace, modificará los recursos disponibles en todas las aplicaciones, no solo en el que está trabajando actualmente.

## <a name="see-also"></a>Vea también

[Notas técnicas por número](../mfc/technical-notes-by-number.md)<br/>
[Notas técnicas por categoría](../mfc/technical-notes-by-category.md)
