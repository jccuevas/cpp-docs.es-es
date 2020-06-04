---
title: 'Cómo: administrar recursos (C++)'
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
ms.openlocfilehash: 0af4e8faeb3d8606fb351b193364a2748fbc944e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80215220"
---
# <a name="how-to-manage-resources-c"></a>Cómo: administrar recursos (C++)

## <a name="copy-and-edit-resources"></a>Copiar y editar recursos

Puede copiar recursos de un archivo a otro sin cambiarlos o cambiar el idioma o la condición de un recurso mientras lo copia.

Puede copiar fácilmente los recursos de un recurso o archivo ejecutable existente en el archivo de recursos actual. Para copiar recursos, abra los dos archivos que contienen recursos al mismo tiempo y arrastre los elementos de un archivo a otro o copie y pegue los dos archivos. Este método funciona para archivos de script de recursos (. RC) y archivos de plantilla de recursos (. RCT), así como archivos ejecutables (. exe).

> [!NOTE]
> Visual C++ incluye archivos de recursos de ejemplo que puede usar en su propia aplicación. Para obtener más información, consulte [CLIPART: Common Resources](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/general).

No se puede arrastrar y colocar, copiar, cortar ni pegar entre archivos de recursos en el proyecto (**vista de recursos**) y los archivos. RC independientes se abren en ventanas de documento. Podría hacer esto en versiones anteriores del producto. Use el método de arrastrar y colocar entre los archivos. RC que están abiertos fuera del proyecto.

### <a name="to-copy-resources"></a>Para copiar recursos

1. Abra ambos archivos de recursos de manera independiente. (Consulte [uso de archivos de script de recursos](how-to-create-a-resource-script-file.md#use-resource-script-files)). Por ejemplo, Abra *Source1. RC* y *source2. RC*.

1. Dentro del primer archivo. rc, puede:

   - Usar el método de arrastrar y colocar

      1. Seleccione el recurso que desea copiar. Por ejemplo, en *Source1. RC*, seleccione **IDD_DIALOG1**.

      1. Mantenga presionada la tecla **Ctrl** y arrastre el recurso al segundo archivo. rc. Por ejemplo, arrastre **IDD_DIALOG1** desde *Source1. RC* a *source2. RC*.

         > [!TIP]
         > Al arrastrar el recurso sin mantener presionada la tecla **Ctrl** , se mueve el recurso en lugar de copiarlo.

   - Usar el método de copiar y pegar

      1. Haga clic con el botón secundario en el recurso con el que desea copiar (por ejemplo, *Source1. RC*) y elija **copiar**.

      1. Haga clic con el botón secundario en el archivo de recursos en el que desea pegar el recurso (por ejemplo, *source2. RC*) y elija **pegar**.

> [!NOTE]
> Para evitar conflictos con nombres de símbolos o valores del archivo existente, visual C++ puede cambiar el valor del símbolo del recurso transferido o el nombre del símbolo y el valor al copiarlo en el nuevo archivo.

Al copiar un recurso, puede cambiar sus propiedades de idioma, condición o ambas.

- El idioma de un recurso especifica el idioma usado por [FindResource](/windows/win32/api/winbase/nf-winbase-findresourcea) para ayudar a identificar el recurso que está buscando. Los recursos pueden tener diferencias para cada idioma que no están relacionados con el texto, por ejemplo, los aceleradores que solo funcionan en un teclado japonés o un mapa de bits que solo sería adecuado para las compilaciones localizadas en chino.

- La condición de un recurso es un símbolo definido que identifica una condición en la que esta copia concreta del recurso se va a utilizar.

El idioma y la condición de un recurso se muestran entre paréntesis después del nombre del recurso en la ventana del **área de trabajo** . Aquí el recurso denominado `IDD_AboutBox` está usando `Finnish` como lenguaje y su condición es `XX33`:

```cpp
IDD_AboutBox (Finnish - XX33)
```

### <a name="to-copy-an-existing-resource-and-change-its-language-or-condition"></a>Para copiar un recurso existente y cambiar su idioma o su condición

En el archivo *. RC* o en la ventana de [vista de recursos](how-to-create-a-resource-script-file.md#create-resources) , haga clic con el botón secundario en el recurso que desea copiar y elija **Insertar copia**. A continuación, establezca lo siguiente:

- En el cuadro de lista **idioma** , seleccione el idioma.

- En el cuadro **condición** , escriba la condición.

### <a name="to-edit-resources"></a>Para editar recursos

Los archivos de recursos administrados (. resx) son archivos XML. Al agregar un archivo de recursos administrado al proyecto desde el cuadro de diálogo **Agregar nuevo elemento** , se abre el **Editor de recursos administrados** de forma predeterminada.

## <a name="import-and-export-resources"></a>Importar y exportar recursos

Puede importar recursos gráficos (mapas de bits, iconos, cursores y barras de herramientas), archivos HTML y recursos personalizados para usarlos en Visual C++. Puede exportar los mismos tipos de archivos de un proyecto de Visual C++ Studio a archivos independientes que se pueden usar fuera del entorno de desarrollo.

> [!NOTE]
> Los tipos de recursos, como los aceleradores, los cuadros de diálogo y las tablas de cadenas, no se pueden importar ni exportar porque no son tipos de archivo independientes.

### <a name="to-import-a-resource-into-the-resource-script-file"></a>Para importar un recurso en el archivo de script de recursos

1. En [vista de recursos](how-to-create-a-resource-script-file.md#create-resources) haga clic con el botón secundario en el nodo del archivo de script de recursos (. RC) al que desea agregar un recurso y seleccione **importar**.

1. Busque y elija el nombre de archivo del mapa de bits (. bmp), el icono (. ico), el cursor (. cur), el archivo HTML (. htm) u otro archivo que desee importar.

1. Seleccione **Aceptar** para agregar el recurso al archivo de script de recursos.

> [!NOTE]
> El proceso de importación funciona de la misma independencia del tipo de recurso que haya seleccionado. El recurso importado se agrega automáticamente al nodo correcto de ese tipo de recurso.

### <a name="to-export-a-resource-for-use-outside-of-visual-c"></a>Para exportar un recurso para usarlo fuera de VisualC++

1. En [vista de recursos](how-to-create-a-resource-script-file.md#create-resources), haga clic con el botón secundario en el recurso que desea exportar y seleccione **exportar**. Puede aceptar el nombre de archivo actual o escribir uno nuevo.

1. Navegue hasta la carpeta en la que desea guardar el archivo y seleccione **exportar**.

## <a name="requirements"></a>Requisitos

Win32

## <a name="see-also"></a>Consulte también

[Archivos de recursos](../windows/resource-files-visual-studio.md)<br/>
[Cómo: crear recursos](../windows/how-to-create-a-resource-script-file.md)<br/>
[Procedimiento para incluir recursos en tiempo de compilación](../windows/how-to-include-resources-at-compile-time.md)
