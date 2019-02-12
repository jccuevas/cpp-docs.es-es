---
title: Filtrar Administrar los recursos (C++)
ms.date: 11/04/2016
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
ms.openlocfilehash: e8b976f974e397b8012ebf59ede08ee64f4f7191
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/12/2019
ms.locfileid: "56150797"
---
# <a name="how-to-manage-resources-c"></a>Filtrar Administrar los recursos (C++)

Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Resources in Desktop Apps](/dotnet/framework/resources/index) en el *Guía del desarrollador de .NET Framework*. Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, acceder a los recursos, mostrar recursos estáticos y asignar cadenas de recursos a propiedades, vea [crear archivos de recursos para las aplicaciones de escritorio](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Para obtener información sobre la globalización y localización de recursos en aplicaciones administradas, vea [Globalizar y localizar aplicaciones de .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="to-copy-resources"></a>Para copiar recursos

Puede copiar los recursos de un archivo a otro sin modificarlas o puede cambiar el idioma o la condición de un recurso al copiarlo.

Puede copiar fácilmente recursos desde un recurso existente o un archivo ejecutable para el archivo de recursos actual. Para copiar los recursos, abra ambos archivos que contienen recursos al mismo tiempo y arrastrar elementos desde un archivo a otro o copiar y pegar entre los dos archivos. Este método funciona para archivos de recursos (.rc) de la secuencia de comandos y archivos de recursos (.rct) de la plantilla y, como archivos ejecutables (.exe).

> [!NOTE]
> Visual C++ incluye archivos de recursos de ejemplo que puede usar en su propia aplicación. Para obtener más información, consulte [CLIPART: Recursos comunes](https://github.com/Microsoft/VCSamples).

Puede usar el método de arrastrar y colocar entre archivos .rc que estén abiertos [fuera del proyecto](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md).

### <a name="to-copy-resources-between-files-using-the-drag-and-drop-method"></a>Para copiar recursos entre archivos mediante el método de arrastrar y colocar

1. Abra ambos archivos de recursos independientes (para obtener más información, consulte [ver recursos en un archivo .rc fuera de un proyecto](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md)). Por ejemplo, abra *Source1.RF* y *Source2.rc*.

1. Dentro del primer archivo .rc, seleccione el recurso que desea copiar. Por ejemplo, en *Source1.RF*, seleccione **IDD_DIALOG1**.

1. Mantenga presionada la **Ctrl** clave y arrastre el recurso para el segundo archivo. rc. Por ejemplo, arrastre **IDD_DIALOG1** desde *Source1.RF* a *Source2.rc*.

   > [!NOTE]
   > Arrastrar el recurso sin mantener presionada la **Ctrl** tecla mueve el recurso, en lugar de copiarlo.

### <a name="to-copy-resources-using-copy-and-paste"></a>Para copiar recursos con copiar y pegar

1. Abra ambos archivos de recursos independientes (para obtener más información, consulte [ver recursos en un archivo .rc fuera de un proyecto](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md)). Por ejemplo, *Source1.RF* y *Source2.rc*.

1. En el archivo de origen desde el que desea copiar un recurso (por ejemplo, *Source1.RF*), haga clic en un recurso y elija **copia** en el menú contextual.

1. Haga clic en el archivo de recursos en la que desea pegar el recurso (por ejemplo, *Source2.rc*). Elija **pegar** en el menú contextual.

   > [!NOTE]
   > No se puede arrastrar y soltar, copiar, cortar o pegar entre archivos de recursos en el proyecto (**vista de recursos**) y archivos .rc independientes (aquellas abiertos en ventanas de documento). Podría hacerlo en las versiones anteriores del producto.

   > [!NOTE]
   > Para evitar conflictos con los nombres de símbolos o valores en el archivo existente, Visual C++ puede cambiar valor de símbolo del recurso transferido o nombre de símbolo y el valor cuando se copia al nuevo archivo.

### <a name="to-change-the-language-or-condition-of-a-resource-while-copying"></a>Para cambiar el idioma o la condición de un recurso al copiarlo

Al copiar un recurso, puede cambiar sus propiedades de idioma, condición o ambas.

- El idioma del recurso identifica exactamente eso, el idioma del recurso. Está usando el lenguaje [FindResource](/windows/desktop/api/winbase/nf-winbase-findresourcea) para ayudar a identificar el recurso que está buscando. (Sin embargo, los recursos pueden tener diferencias para cada idioma que no estén relacionados con texto, por ejemplo, se compila aceleradores que solo funcionen en teclados japoneses o un mapa de bits que solo sea adecuado para localizadas en chino).

- La condición de un recurso es un símbolo definido que identifica una condición en la que esta copia concreta del recurso se va a utilizar.

El idioma y la condición de un recurso se muestran entre paréntesis después del nombre del recurso en el **área de trabajo** ventana. En este ejemplo, el recurso denominado `IDD_AboutBox` usa `Finnish` como su idioma y su condición es `XX33`.

```cpp
IDD_AboutBox (Finnish - XX33)
```

Para copiar un recurso existente y cambiar su idioma o condición:

1. En el archivo .rc o en la [vista de recursos](../windows/resource-view-window.md) ventana, haga clic en el recurso que van a copiar.

1. Elija **Insertar copia** en el menú contextual.

1. En el **Insertar copia de recursos** cuadro de diálogo:

   - Para el **lenguaje** cuadro de lista, seleccione el idioma.

   - En el **condición** , escriba la condición.

## <a name="to-edit-managed-resource-files"></a>Para editar archivos de recursos administrados

Archivos de recursos administrados (.resx) son archivos XML. Cuando agrega un archivo de recursos administrado al proyecto desde el **Agregar nuevo elemento** cuadro de diálogo, el **Editor de recursos administrados** se abre de forma predeterminada.

## <a name="to-import-and-export-resources"></a>Para importar y exportar recursos

Puede importar recursos gráficos (mapas de bits, iconos, cursores y barras de herramientas), archivos HTML y recursos personalizados para usarlos en Visual C++. Puede exportar los mismos tipos de archivos desde un proyecto de Visual C++ para separar archivos que se pueden usar fuera del entorno de desarrollo.

> [!NOTE]
> Los tipos de recursos como los aceleradores, los cuadros de diálogo y las tablas de cadenas no se pueden importar o exportar, porque no son tipos de archivos independientes.

### <a name="to-import-an-individual-resource-into-your-current-resource-file"></a>Para importar un recurso individual al archivo de recursos actual

1. En [vista de recursos](../windows/resource-view-window.md), haga clic en el nodo para el script de recursos (* .rc) a la que desea agregar un recurso de archivo.

1. Seleccione **importación** en el menú contextual.

1. Busque y seleccione el nombre de archivo del mapa de bits (.bmp), icono (.ico), cursor (.cur), archivo Html (.htm) o cualquier otro archivo que quiera importar.

1. Elija **Aceptar** para agregar el recurso al archivo seleccionado en **recursos** vista.

   > [!NOTE]
   > El proceso de importación es el mismo, independientemente del tipo de recurso seleccionado. El recurso importado se agrega automáticamente al nodo correspondiente a ese tipo de recurso.

### <a name="to-export-a-bitmap-icon-or-cursor-as-a-separate-file-for-use-outside-of-visual-c"></a>Para exportar un mapa de bits, un icono o un cursor como un archivo independiente (para usarlo fuera de Visual C++)

1. En **recursos** ver, haga clic en el recurso que desea exportar.

1. Seleccione **exportar** en el menú contextual.

1. En el **Exportar recurso** diálogo cuadro, acepte el nombre de archivo actual o escriba uno nuevo.

1. Navegue hasta la carpeta donde desea guardar el archivo y elija **exportar**.

## <a name="requirements"></a>Requisitos

Win32

## <a name="see-also"></a>Vea también

[Archivos de recursos](../windows/resource-files-visual-studio.md)<br/>
[Editores de recursos](../windows/resource-editors.md)