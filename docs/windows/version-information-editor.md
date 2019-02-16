---
title: Editor de información de versión (C++)
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
ms.openlocfilehash: 8420feb6ddde116a24bee5333f4ef8f83ff4e0d4
ms.sourcegitcommit: 470de1337035dd33682d935b4b6c6d8b1bdb0bbb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/15/2019
ms.locfileid: "56320476"
---
# <a name="version-information-editor-c"></a>Editor de información de versión (C++)

La información de versión consta de la identificación del producto y la empresa, un número de versión del producto, y la notificación de copyright y marca comercial. Con el **información de versión** editor, crear y mantener estos datos, que se almacenan en el recurso de información de versión. No se requiere el recurso de información de versión por una aplicación, pero es un lugar útil para recopilar información que identifica la aplicación. También se usa la información de versión por las API de instalación.

Un recurso de información de versión tiene un bloque superior y uno o más bloques inferiores: un único bloque de información fija en la parte superior y uno o más bloques de información de versión en la parte inferior (para otros idiomas o juegos de caracteres). El bloque superior tiene tanto cuadros numéricos editables como listas desplegables seleccionables. Los bloques inferiores solo tienen cuadros de texto editables.

> [!NOTE]
> El estándar de Windows es tener únicamente un recurso de versión, llamado VS_VERSION_INFO.

## <a name="how-to"></a>Tema de procedimientos

El **información de versión** editor le permite:

### <a name="to-edit-a-string-in-a-version-information-resource"></a>Para editar una cadena en un recurso de información de versión

Seleccione el elemento una vez para, a continuación, vuelva a seleccionarla para comenzar a editarlo. Realice los cambios directamente en el **información de versión** tabla o en el [ventana propiedades](/visualstudio/ide/reference/properties-window). Los cambios que realice se reflejarán en ambos lugares.

Cuando se edita la `FILEFLAGS` clave en el **información de versión** editor, observará que no se puede establecer el **depurar**, **compilación privada**, o **especiales Compilar** propiedades (en el **propiedades** ventana) para archivos. rc:

- El **información de versión** editor establece la **depurar** propiedad con un `#ifdef` en el script de recursos, según la `_DEBUG` marca de compilación.

- Si el `Private Build` clave tiene un **valor** establecido el **información de versión** de tabla, la correspondiente **compilación privada** propiedad (en el **propiedades**  ventana) para el `FILEFLAGS` clave será **True**. Si el **Valor** está vacío, la propiedad será **False**. Del mismo modo, el **Special Build** clave (en el **información de versión** tabla) está asociado a la **Special Build** propiedad para el `FILEFLAGS` clave.

Puede ordenar la secuencia de información del bloque de cadena con un clic en el **clave** o **valor** encabezados de columna. Estos encabezados reorganizan automáticamente la información en la secuencia seleccionada.

### <a name="to-add-version-information-for-another-language-new-version-info-block"></a>Para agregar información de versión para otro idioma (nuevo bloque de información de versión)

1. Para abrir un recurso de información de versión, haga doble clic en él en la [Vista de recursos](../windows/resource-view-window.md).

1. Haga clic con el botón secundario dentro de la tabla de información de versión y elija **Nuevo bloque de información de versión** en el menú contextual.

   Este comando agrega un bloque de información adicional al recurso de información de versión actual y abre sus propiedades correspondientes en la [ventana Propiedades](/visualstudio/ide/reference/properties-window).

1. En la ventana **Propiedades** , elija el idioma apropiado y el juego de caracteres para su nuevo bloque.

### <a name="to-delete-a-version-information-block"></a>Para eliminar un bloque de información de versión

1. Para abrir el recurso de información de versión, haga doble clic en su icono en la [Vista de recursos](../windows/resource-view-window.md).

1. Haga clic en el encabezado de bloque que quiera eliminar y después elija **Eliminar bloque de información de versión** en el menú contextual.

   Este comando elimina el encabezado seleccionado y deja intacto el resto de la información de versión. No se puede deshacer la acción.

### <a name="to-access-version-information-from-within-your-program"></a>Para obtener acceso a la información de versión desde dentro de su programa

Si quiere tener acceso a la información de versión desde su programa, use la función [GetFileVersionInfo](/windows/desktop/api/winver/nf-winver-getfileversioninfoa) y la función [VerQueryValue](/windows/desktop/api/winver/nf-winver-verqueryvaluea) .

   > [!NOTE]
   > Al usar el **información de versión** editor, en muchos casos, puede hacer clic en para mostrar un menú contextual de comandos específicos del recurso. Por ejemplo, si selecciona mientras se apunta a una entrada de encabezado de bloque, el menú contextual muestra los **nueva información de bloque de versión** y **eliminar información del bloque de versión** comandos.

## <a name="requirements"></a>Requisitos

Win32

## <a name="see-also"></a>Vea también

[Editores de recursos](../windows/resource-editors.md)<br/>
[Menús y otros recursos](https://msdn.microsoft.com/library/windows/desktop/ms632583.aspx)<br/>
[Información de versiones (Windows)](https://msdn.microsoft.com/library/windows/desktop/ms646981.aspx)
