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
ms.openlocfilehash: 955cce012ac30c3413d7d458e263643d0aefa711
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84615352"
---
# <a name="binary-editor-c"></a>Editor binario (C++)

> [!CAUTION]
> Es peligroso editar recursos como cuadros de diálogo, imágenes o menús en el **Editor binario** . Una edición incorrecta podría dañar el recurso y hacerlo ilegible en su editor nativo.

El **Editor binario** permite editar cualquier recurso en el nivel binario en formato hexadecimal o ASCII. También se puede utilizar el [comando Buscar](/visualstudio/ide/reference/find-command) para buscar cadenas ASCII o bytes hexadecimales. Use el **Editor binario** solo cuando necesite ver o realizar pequeños cambios en recursos personalizados o en tipos de recursos no admitidos por el entorno de Visual Studio. El **Editor binario** no está disponible en las ediciones Express.

- Para abrir el **Editor binario** en un archivo nuevo, vaya a menú **archivo**  >  **nuevo**  >  **archivo**, seleccione el tipo de archivo que desea editar, seleccione la flecha de lista desplegable situada junto al botón **abrir** y elija **abrir con**el  >  **Editor binario**.

- Para abrir el **Editor binario** en un archivo existente, vaya a menú **archivo**  >  **abrir**  >  **archivo**, seleccione el archivo que desea editar, haga clic en la flecha de lista desplegable situada junto al botón **abrir** y elija **abrir con**el  >  **Editor binario**.

   ![Editor binario](../mfc/media/vcbinaryeditor2.gif "vcBinaryEditor2")<br/>
   Datos binarios de un cuadro de diálogo mostrado en el **Editor binario**

Solo determinados valores ASCII se representan en el **Editor binario** (de 0X20 a 0x7e). Los caracteres extendidos se muestran como puntos en la sección del valor ASCII del panel derecho del **Editor binario**. Los caracteres imprimibles son valores ASCII de 32 a 126.

> [!TIP]
> Al usar el **Editor binario**, en muchos casos puede hacer clic con el botón secundario para mostrar un menú contextual de comandos específicos de recursos. Los comandos disponibles dependen del objeto al que apunta el cursor. Por ejemplo, si hace clic con el botón secundario mientras apunta al **Editor binario** con valores hexadecimales seleccionados, el menú contextual muestra los comandos **cortar**, **copiar**y **pegar** .

## <a name="how-to"></a>Procedimientos

El **Editor binario** le permite:

### <a name="to-open-a-windows-desktop-resource-for-binary-editing"></a>Para abrir un recurso de escritorio de Windows para editarlo en modo binario

1. En la [Vista de recursos](how-to-create-a-resource-script-file.md#create-resources), seleccione el archivo de recursos específico que quiera editar.

1. Haga clic con el botón secundario en el recurso y seleccione **abrir datos binarios**.

> [!NOTE]
> Si usa la ventana de **vista de recursos** para abrir un recurso con un formato que Visual Studio no reconozca, como RCDATA o un recurso personalizado, el recurso se abrirá automáticamente en el **Editor binario**.

### <a name="to-open-a-managed-resource-for-binary-editing"></a>Para abrir un recurso para editarlo para la edición binaria

1. En **Explorador de soluciones**, seleccione el archivo de recursos específico que desea editar.

1. Haga clic con el botón derecho en el recurso y seleccione **abrir con**.

1. En el cuadro de diálogo **Abrir con** , seleccione **Editor binario**.

> [!NOTE]
> Puede usar el [Editor de imágenes](image-editor-for-icons.md) y el **Editor binario** para trabajar con archivos de recursos en proyectos administrados. Todos los recursos administrados que vaya a editar deberán estar vinculados. Los editores de recursos de Visual Studio no admiten la edición de recursos incrustados.

### <a name="to-edit-a-resource"></a>Para editar un recurso

Si desea usar el **Editor binario** en un recurso que ya se está editando en otra ventana del editor, cierre primero la otra ventana del editor.

1. Seleccione el byte que desea editar.

   La tecla **Tab** mueve el foco entre las secciones hexadecimal y ASCII del **Editor binario**. Puede utilizar las teclas **re** pág y **Av Pág** para desplazarse por el recurso una pantalla a la vez.

1. Escriba el nuevo valor.

   El valor cambia inmediatamente en las secciones hexadecimal y ASCII y el foco se desplaza al siguiente valor de la línea.

> [!NOTE]
> El **Editor binario** acepta los cambios automáticamente al cerrar el editor.

### <a name="to-find-binary-data"></a>Para buscar datos binarios

Puede buscar cadenas ASCII o bytes hexadecimales. Por ejemplo, para buscar *Hola*, puede buscar la cadena *Hello* o su valor hexadecimal, *48 65 6C 6C 6F*.

1. Vaya a menú **Editar**  >  [Buscar](/visualstudio/ide/reference/find-command).

1. En el cuadro **Buscar** , seleccione una cadena de búsqueda anterior en la lista desplegable o escriba los datos que desea buscar.

1. Seleccione cualquiera de las opciones de **búsqueda** y elija **Buscar siguiente**.

### <a name="to-create-a-new-custom-or-data-resource"></a>Para crear un nuevo recurso personalizado o de datos

Puede crear un nuevo recurso personalizado o de datos colocando el recurso en un archivo independiente mediante la sintaxis de archivo de script de recursos (. RC) normal y, a continuación, incluyendo ese archivo haciendo clic con el botón derecho en el proyecto en **Explorador de soluciones** y seleccionando archivos de **inclusión de recursos**.

1. [Cree un archivo .rc](how-to-create-a-resource-script-file.md) que contenga el recurso personalizado o de datos.

   Puede escribir datos personalizados en un archivo .rc como cadenas entre comillas terminadas en null o como enteros en formato octal, hexadecimal o decimal.

1. En **Explorador de soluciones**, haga clic con el botón secundario en el archivo. rc del proyecto y seleccione archivos de **inclusión de recursos**.

1. En el cuadro **directivas de tiempo de compilación** , escriba una `#include` instrucción que proporcione el nombre del archivo que contiene el recurso personalizado, por ejemplo:

    ```cpp
    #include mydata.rc
    ```

   Asegúrese de que la sintaxis y la ortografía de lo que escribe son correctas. El contenido del cuadro **directivas de tiempo de compilación** se inserta en el archivo de script de recursos exactamente como se escribe.

1. Seleccione **Aceptar** para registrar los cambios.

Otra forma de crear un recurso personalizado es importar un archivo externo como recurso personalizado, vea [Cómo: administrar recursos](../windows/how-to-import-and-export-resources.md).

> [!NOTE]
> La creación de nuevos recursos de datos o personalizados requiere Win32.

## <a name="requirements"></a>Requisitos

None

## <a name="see-also"></a>Consulte también

[Editores de recursos](resource-editors.md)
