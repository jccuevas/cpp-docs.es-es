---
title: Filtrar Administrar los recursos (C++)
ms.date: 02/14/2019
f1_keywords:
- vc.resvw.resource.copying
- vs.resvw.resource.copying
- vc.resvw.resource.changing
- vb.xmldesigner.data
- vs.resvw.resource.importing
- vc.resvw.resource.importing
helpviewer_keywords:
- resources [C++], moving between files
- resources [C++], copying
- resource files [C++], copying or moving resources between
- resource files [C++], tiling
- .rc files [C++], copying resources between
- rc files [C++], copying resources between
- Language property [C++]
- .resx files [C++], editing
- resource files [C++], editing
- resx files [C++], editing
- resources [C++], exporting
- graphics [C++], exporting
- graphics [C++], importing
- resources [C++], importing
- bitmaps [C++], importing and exporting
- toolbars [C++], importing
- images [C++], importing
- toolbars [C++], exporting
- cursors [C++], importing and exporting
- images [C++], exporting
ms.assetid: 65f523e8-017f-4fc6-82d1-083c56d9131f
ms.openlocfilehash: 9867fdf260750d47421e699cdd0d7a58b02ce947
ms.sourcegitcommit: c1f646c8b72f330fa8cf5ddb0f8f261ba10d16f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2019
ms.locfileid: "58328628"
---
# <a name="how-to-manage-resources-c"></a>Procedimiento Administrar los recursos (C++)

## <a name="copy-and-edit-resources"></a>Copiar y editar recursos

Puede copiar los recursos de un archivo a otro sin modificarlas o cambiar el idioma o la condición de un recurso al copiarlo.

Puede copiar fácilmente recursos desde un recurso existente o un archivo ejecutable para el archivo de recursos actual. Para copiar los recursos, abra ambos archivos que contienen recursos al mismo tiempo y arrastrar elementos desde un archivo a otro o copiar y pegar entre los dos archivos. Este método funciona para archivos de recursos (.rc) de la secuencia de comandos y archivos de recursos (.rct) de la plantilla y, como archivos ejecutables (.exe).

> [!NOTE]
> Visual C++ incluye archivos de recursos de ejemplo que puede usar en su propia aplicación. Para obtener más información, consulte [CLIPART: Recursos comunes](https://github.com/Microsoft/VCSamples).

No se puede arrastrar y soltar, copiar, cortar o pegar entre archivos de recursos en el proyecto (**vista de recursos**) y abren los archivos .rc independientes en las ventanas de documento. Podría hacerlo en las versiones anteriores del producto. Solo puede usar el método de arrastrar y colocar entre archivos .rc que estén abiertos fuera del proyecto.

### <a name="to-copy-resources"></a>Para copiar recursos

1. Abra ambos archivos de recursos de manera independiente. (Consulte [usan archivos de script de recursos](how-to-create-a-resource-script-file.md#use-resource-script-files)). Por ejemplo, abra *Source1.RF* y *Source2.rc*.

1. En el primer archivo .rc, ya sea:

   - Utilice el método de arrastrar y colocar

      1. Seleccione el recurso que desea copiar. Por ejemplo, en *Source1.RF*, seleccione **IDD_DIALOG1**.

      1. Mantenga presionada la **Ctrl** clave y arrastre el recurso para el segundo archivo. rc. Por ejemplo, arrastre **IDD_DIALOG1** desde *Source1.RF* a *Source2.rc*.

         > [!TIP]
         > Arrastrar el recurso sin mantener presionada la **Ctrl** tecla mueve el recurso, en lugar de copiarlo.

   - Usar la copia y pegue el método

      1. Haga clic en el recurso con copiar (por ejemplo, *Source1.RF*) y elija **copia**.

      1. Haga clic en el archivo de recursos en la que desea pegar el recurso (por ejemplo, *Source2.rc*) y elija **pegar**.

> [!NOTE]
> Para evitar conflictos con los nombres de símbolos o valores en el archivo existente, Visual C++ puede cambiar valor de símbolo del recurso transferido o nombre de símbolo y el valor cuando se copia al nuevo archivo.

Al copiar un recurso, puede cambiar sus propiedades de idioma, condición o ambas.

- El idioma de un recurso especifica el idioma usado por [FindResource](/windows/desktop/api/winbase/nf-winbase-findresourcea) para ayudar a identificar el recurso que está buscando. Los recursos pueden tener diferencias para cada idioma que no estén relacionados con texto, por ejemplo, las compilaciones aceleradores que solo funcionen en teclados japoneses o un mapa de bits que solo sea adecuado para localizadas en chino.

- La condición de un recurso es un símbolo definido que identifica una condición en la que esta copia concreta del recurso se va a utilizar.

El idioma y la condición de un recurso se muestran entre paréntesis después del nombre del recurso en el **área de trabajo** ventana. Aquí el recurso denominado `IDD_AboutBox` usa `Finnish` como su idioma y su condición es `XX33`:

```cpp
IDD_AboutBox (Finnish - XX33)
```

### <a name="to-copy-an-existing-resource-and-change-its-language-or-condition"></a>Para copiar un recurso existente y cambiar su idioma o su condición

En el *.rc* archivo o en el [vista de recursos](how-to-create-a-resource-script-file.md#create-resources) ventana, haga clic en el recurso que desea copiar y elija **Insertar copia**. A continuación, establezca lo siguiente:

- Para el **lenguaje** cuadro de lista, seleccione el idioma.

- En el **condición** , escriba la condición.

### <a name="to-edit-resources"></a>Para editar recursos

Archivos de recursos administrados (.resx) son archivos XML. Cuando agrega un archivo de recursos administrado al proyecto desde el **Agregar nuevo elemento** cuadro de diálogo, el **Editor de recursos administrados** se abre de forma predeterminada.

## <a name="import-and-export-resources"></a>Importar y exportar recursos

Puede importar recursos gráficos (mapas de bits, iconos, cursores y barras de herramientas), archivos HTML y recursos personalizados para usarlos en Visual C++. Puede exportar los mismos tipos de archivos desde un proyecto de Visual C++ para separar archivos que se pueden usar fuera del entorno de desarrollo.

> [!NOTE]
> Tipos de recursos como los aceleradores, los cuadros de diálogo y las tablas de cadenas no se pueden importar o exportar porque no son tipos de archivos independientes.

### <a name="to-import-a-resource-into-the-resource-script-file"></a>Para importar un recurso en el archivo de script de recursos

1. En [vista de recursos](how-to-create-a-resource-script-file.md#create-resources) haga clic en el nodo del archivo de script (.rc) de recursos al que desea agregar un recurso y seleccione **importación**.

1. Busque y seleccione el nombre de archivo de mapa de bits (.bmp), icono (.ico), cursor (.cur), el archivo html (.htm) u otro archivo para importar.

1. Seleccione **Aceptar** para agregar el recurso al archivo de script de recursos.

> [!NOTE]
> El proceso de importación funciona igual importar el tipo de recurso no ha seleccionado. El recurso importado se agrega automáticamente al nodo correcto de ese tipo de recurso.

### <a name="to-export-a-resource-for-use-outside-of-visual-c"></a>Para exportar un recurso para su uso fuera de Visual C++

1. En [vista de recursos](how-to-create-a-resource-script-file.md#create-resources), haga clic en el recurso que desea exportar y seleccione **exportar**. Puede aceptar el nombre de archivo actual o escriba uno nuevo.

1. Navegue hasta la carpeta donde desea guardar el archivo y seleccione **exportar**.

## <a name="requirements"></a>Requisitos

Win32

## <a name="see-also"></a>Vea también

[Archivos de recursos](../windows/resource-files-visual-studio.md)<br/>
[Cómo: Crear recursos](../windows/how-to-create-a-resource-script-file.md)<br/>
[Cómo: Incluir recursos en tiempo de compilación](../windows/how-to-include-resources-at-compile-time.md)<br/>