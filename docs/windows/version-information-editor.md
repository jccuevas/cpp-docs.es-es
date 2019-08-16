---
title: Editor de información deC++versión ()
ms.date: 02/14/2019
f1_keywords:
- vc.editors.version.F1
- vc.editors.version
helpviewer_keywords:
- Version Information editor [C++], about Version Information editor
- editors, Version Information
- resource editors [C++], Version Information editor
- version information resources [C++]
- resources [C++], editing version information
- languages, version information
- New Version Info Block
- blocks, adding
- resources [C++], adding version information
- version information, adding for languages
- blocks, deleting
- version information, deleting blocks
- resources [C++], deleting version information
- VerQueryValue
- version information, accessing from within programs
- GetFileVersionInfo
- version information
ms.assetid: 772e6f19-f765-4cec-9521-0ad3eeb99f9b
ms.openlocfilehash: e68e1480d2cd9a8d8a4d862252e6eb4384a5cd68
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69513644"
---
# <a name="version-information-editor-c"></a>Editor de información deC++versión ()

La información de versión consta de la identificación del producto y la empresa, un número de versión del producto, y la notificación de copyright y marca comercial. Con el **Editor de información de versión**, crea y mantiene estos datos, que se almacenan en el recurso de información de versión. Una aplicación no requiere el recurso de información de versión, pero es un lugar útil para recopilar información que identifica la aplicación. También se usa la información de versión por las API de instalación.

> [!NOTE]
> El estándar de Windows es tener únicamente un recurso de versión, llamado VS_VERSION_INFO.

Un recurso de información de versión tiene un bloque superior y uno o más bloques inferiores: un único bloque de información fija en la parte superior y uno o más bloques de información de versión en la parte inferior (para otros idiomas o juegos de caracteres). El bloque superior tiene tanto cuadros numéricos editables como listas desplegables seleccionables. Los bloques inferiores solo tienen cuadros de texto editables.

> [!NOTE]
> Al usar el **Editor de información de versión**, en muchos casos puede hacer clic con el botón secundario para mostrar un menú contextual de comandos específicos de recursos. Por ejemplo, si selecciona mientras apunta a una entrada de encabezado de bloque, el menú contextual muestra los comandos **nueva información de bloque de versión** y **eliminar información de bloque de versión** .

## <a name="how-to"></a>Procedimientos

El **Editor de información de versión** le permite:

### <a name="to-edit-a-string-in-a-version-information-resource"></a>Para editar una cadena en un recurso de información de versión

Seleccione el elemento una vez para seleccionarlo y, a continuación, vuelva a empezar a editarlo. Realice los cambios directamente en la tabla de **información de versión** o en el [ventana Propiedades](/visualstudio/ide/reference/properties-window). Los cambios que realice se reflejarán en ambos lugares.

Al editar la `FILEFLAGS` clave en el **Editor de información de versión**, tenga en cuenta que no puede establecer las propiedades depuración, **compilación privada**o **compilación especial** en la ventana **propiedades** de los archivos. RC:

   - El **Editor de información de versión** establece la propiedad **Debug** con un `#ifdef` en el script de recursos, basado en la `_DEBUG` marca de compilación.

  - Si la `Private Build` clave tiene un **valor** establecido en la tabla de **información de versión** , la propiedad de **compilación privada** correspondiente en la ventana `FILEFLAGS` **propiedades** de la clave será **true**. Si el **valor** está vacío, la propiedad será **false**. Del mismo modo, la clave de **compilación especial** en la tabla de **información de versión** está vinculada a `FILEFLAGS` la propiedad de **compilación especial** para la clave.

Puede ordenar la secuencia de información del bloque de cadena seleccionando los encabezados de columna **clave** o **valor** . Estos encabezados reorganizan automáticamente la información en la secuencia seleccionada.

### <a name="to-add-version-information-for-another-language-new-version-info-block"></a>Para agregar información de versión para otro idioma (nuevo bloque de información de versión)

1. Para abrir un recurso de información de versión, haga doble clic en él en la [Vista de recursos](how-to-create-a-resource-script-file.md#create-resources).

1. Haga clic con el botón derecho en la tabla información de versión y elija **nuevo bloque de información de versión**.

   Este comando agrega un bloque de información adicional al recurso de información de versión actual y abre sus propiedades correspondientes en la [ventana Propiedades](/visualstudio/ide/reference/properties-window).

1. En la ventana **Propiedades** , elija el idioma apropiado y el juego de caracteres para su nuevo bloque.

### <a name="to-delete-a-version-information-block"></a>Para eliminar un bloque de información de versión

1. Para abrir el recurso de información de versión, haga doble clic en su icono en la [Vista de recursos](how-to-create-a-resource-script-file.md#create-resources).

1. Haga clic con el botón derecho en el encabezado de bloque que quiera eliminar y elija **eliminar bloque de información de versión**.

   Este comando elimina el encabezado seleccionado y deja intacto el resto de la información de versión. No se puede deshacer la acción.

### <a name="to-access-version-information-from-within-your-program"></a>Para obtener acceso a la información de versión desde dentro de su programa

Si quiere tener acceso a la información de versión desde su programa, use la función [GetFileVersionInfo](/windows/win32/api/winver/nf-winver-getfileversioninfow) y la función [VerQueryValue](/windows/win32/api/winver/nf-winver-verqueryvaluew) .

## <a name="requirements"></a>Requisitos

Win32

## <a name="see-also"></a>Vea también

[Editores de recursos](../windows/resource-editors.md)<br/>
[Menús y otros recursos](/windows/win32/menurc/resources)<br/>
[Información de versiones (Windows)](/windows/win32/menurc/version-information)
