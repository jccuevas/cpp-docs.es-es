---
title: Editor binario (C++)
ms.date: 02/14/2019
f1_keywords:
- vc.editors.binary.F1
- vc.editors.binary
helpviewer_keywords:
- editors, Binary
- resources [C++], editing
- resource editors [C++], Binary editor
- Binary editor
- binary data, editing
- resources [C++], opening for binary editing
- binary data
- hexadecimal bytes in binary data
- strings [C++], searching for
- file searches [C++]
- binary data, finding
- ASCII characters, finding in binary data
- custom resources [C++]
- data resources [C++]
- resources [C++], creating
ms.assetid: 2483c48b-1252-4dbc-826b-82e6c1a0e9cb
ms.openlocfilehash: 832dbf711307b81527bcaff0d1e1b8138f208e46
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62407044"
---
# <a name="binary-editor-c"></a>Editor binario (C++)

> [!CAUTION]
> Modificar recursos, como cuadros de diálogo, imágenes o menús en la **Editor binario** es peligroso. Una edición incorrecta podría dañar el recurso y hacerlo ilegible en su editor nativo.

El **Editor binario** permite editar cualquier recurso en el nivel binario en formato ASCII o hexadecimal. También se puede utilizar el [comando Buscar](/visualstudio/ide/reference/find-command) para buscar cadenas ASCII o bytes hexadecimales. Use la **Editor binario** sólo cuando necesite ver o realizar menores cambia a los recursos personalizados o tipos de recursos no admitidos en el entorno de Visual Studio. El **Editor binario** no está disponible en las ediciones Express.

- Para abrir el **Editor binario** en un nuevo archivo, vaya al menú **archivo** > **New** > **archivo**, seleccione el tipo de archivo que desea editar y luego seleccione la flecha desplegable situada junto a la **abierto** botón y elija **abrir con** > **Editor binario**.

- Para abrir el **Editor binario** en un archivo existente, vaya al menú **archivo** > **abrir** > **archivo**, seleccione el archivo que desea editar y luego seleccione la flecha desplegable situada junto a la **abierto** botón y elija **abrir con** > **Editor binario**.

   ![Editor binario](../mfc/media/vcbinaryeditor2.gif "vcBinaryEditor2")<br/>
   Datos binarios de un cuadro de diálogo que se muestra en el **Editor binario**

Solo determinados valores ASCII se representan en el **Editor binario** (0 x 20 a 0x7E). Los caracteres extendidos se muestran como puntos en la sección de valor ASCII de panel derecho de la **Editor binario**. Los caracteres imprimibles son valores ASCII 32 a 126.

> [!TIP]
> Al usar el **Editor binario**, en muchos casos hacer clic en para mostrar un menú contextual de comandos específicos del recurso. Los comandos disponibles dependen del objeto al que apunta el cursor. Por ejemplo, si hace clic mientras se apunta a la **Editor binario** teniendo seleccionados valores hexadecimales, el menú contextual muestra los **cortar**, **copia**y **Pegar** comandos.

## <a name="how-to"></a>Procedimientos

El **Editor binario** le permite:

### <a name="to-open-a-windows-desktop-resource-for-binary-editing"></a>Para abrir un recurso de escritorio de Windows para editarlo en modo binario

1. En la [Vista de recursos](how-to-create-a-resource-script-file.md#create-resources), seleccione el archivo de recursos específico que quiera editar.

1. Haga clic en el recurso y seleccione **abrir datos binarios**.

> [!NOTE]
> Si usas el **vista de recursos** ventana para abrir un recurso con un formato que Visual Studio no reconoce, como RCDATA o un recurso personalizado, el recurso se abrirá automáticamente en el **Editor binario**.

### <a name="to-open-a-managed-resource-for-binary-editing"></a>Para abrir un recurso para editarlo para la edición binaria

1. En **el Explorador de soluciones**, seleccione el archivo de recursos específico que desea editar.

1. Haga clic en el recurso y seleccione **abrir con**.

1. En el cuadro de diálogo **Abrir con** , seleccione **Editor binario**.

> [!NOTE]
> Puede usar el [Editor de imágenes](../windows/image-editor-for-icons.md) y **Editor binario** para trabajar con archivos de recursos en proyectos administrados. Todos los recursos administrados que vaya a editar deberán estar vinculados. Los editores de recursos de Visual Studio no admiten la edición de recursos incrustados.

### <a name="to-edit-a-resource"></a>Para editar un recurso

Si desea usar el **Editor binario** en un recurso que ya se está editando en otra ventana del editor, cierre primero la otra ventana del editor.

1. Seleccione el byte que se va a editar.

   El **ficha** tecla mueve el foco entre las secciones hexadecimal y ASCII de la **Editor binario**. Puede usar el **RE PÁG** y **AV PÁG** teclas para desplazarse por los recursos de la pantalla a la vez.

1. Escriba el nuevo valor.

   El valor cambia inmediatamente en las secciones de ASCII y hexadecimales y foco se desplaza hasta el siguiente valor en línea.

> [!NOTE]
> El **Editor binario** acepta los cambios automáticamente al cerrar el editor.

### <a name="to-find-binary-data"></a>Para buscar datos binarios

Puede buscar cadenas ASCII o bytes hexadecimales. Por ejemplo, para buscar *Hello*, se puede buscar la cadena *Hello* o su valor hexadecimal, *48 65 6C 6C 6F*.

1. Vaya al menú **editar** > [encontrar](/visualstudio/ide/reference/find-command).

1. En el **buscar** cuadro, seleccione una cadena de búsqueda anterior en la lista desplegable o escriba los datos que desea buscar.

1. Seleccione cualquiera de los **buscar** opciones y elegir **Buscar siguiente**.

### <a name="to-create-a-new-custom-or-data-resource"></a>Para crear un nuevo recurso personalizado o de datos

Puede crear un nuevo recurso personalizado o de datos, coloque el recurso en un archivo independiente con sintaxis normal de recursos (.rc) de la secuencia de comandos archivo y, a continuación, incluya ese archivo haciendo clic con el proyecto en **el Explorador de soluciones** y seleccionando  **Inclusión de recursos**.

1. [Cree un archivo .rc](../windows/how-to-create-a-resource-script-file.md) que contenga el recurso personalizado o de datos.

   Puede escribir datos personalizados en un archivo .rc como cadenas entre comillas terminadas en null o como enteros en formato octal, hexadecimal o decimal.

1. En **el Explorador de soluciones**, haga clic en el archivo .rc de su proyecto y seleccione **incluye recursos**.

1. En el **Rectivas de tiempo** , escriba un `#include` instrucción que proporciona el nombre del archivo que contiene el recurso personalizado, por ejemplo:

    ```cpp
    #include mydata.rc
    ```

   Asegúrese de que la sintaxis y la ortografía de lo que escribe son correctas. El contenido de la **Rectivas de tiempo** cuadro se insertan en el archivo de script de recursos exactamente como se escribieron.

1. Seleccione **Aceptar** para registrar sus cambios.

Otra forma de crear un recurso personalizado es importar un archivo externo como recurso personalizado, consulte [Cómo: Administrar recursos](../windows/how-to-import-and-export-resources.md).

> [!NOTE]
> Creación de nuevos recursos personalizado o de datos requiere Win32.

## <a name="requirements"></a>Requisitos

Ninguna

## <a name="see-also"></a>Vea también

[Editores de recursos](../windows/resource-editors.md)