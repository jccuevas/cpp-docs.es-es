---
title: Filtrar Copiar recursos (C++)
ms.date: 11/04/2016
f1_keywords:
- vc.resvw.resource.copying
- vs.resvw.resource.copying
- vc.resvw.resource.changing
helpviewer_keywords:
- resources [C++], moving between files
- resources [C++], copying
- resource files [C++], copying or moving resources between
- resource files [C++], tiling
- .rc files [C++], copying resources between
- rc files [C++], copying resources between
- Language property [C++]
ms.assetid: 65f523e8-017f-4fc6-82d1-083c56d9131f
ms.openlocfilehash: 772c9b905d4cb0c4e2ccab9ec51aa02860b2db32
ms.sourcegitcommit: bd637e9c39650cfd530520ea978a22fa4caa0e42
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/07/2019
ms.locfileid: "55849666"
---
# <a name="how-to-copy-resources-c"></a>Filtrar Copiar recursos (C++)

Puede copiar los recursos de un archivo a otro sin modificarlas o puede cambiar el idioma o la condición de un recurso al copiarlo.

Puede copiar fácilmente recursos desde un recurso existente o un archivo ejecutable para el archivo de recursos actual. Para copiar los recursos, abra ambos archivos que contienen recursos al mismo tiempo y arrastrar elementos desde un archivo a otro o copiar y pegar entre los dos archivos. Este método funciona para archivos de recursos (.rc) de la secuencia de comandos y archivos de recursos (.rct) de la plantilla y, como archivos ejecutables (.exe).

> [!NOTE]
> Visual C++ incluye archivos de recursos de ejemplo que puede usar en su propia aplicación. Para obtener más información, consulte [CLIPART: Recursos comunes](https://github.com/Microsoft/VCSamples).

Puede usar el método de arrastrar y colocar entre archivos .rc que estén abiertos [fuera del proyecto](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md).

## <a name="to-copy-resources-between-files-using-the-drag-and-drop-method"></a>Para copiar recursos entre archivos mediante el método de arrastrar y colocar

1. Abra ambos archivos de recursos independientes (para obtener más información, consulte [ver recursos en un archivo fuera de un proyecto de .rc](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md)). Por ejemplo, abra Source1.rf y Source2.rc.

1. Dentro del primer archivo .rc, seleccione el recurso que desea copiar. Por ejemplo, en `Source1.rc`, seleccione **IDD_DIALOG1**.

1. Mantenga presionada la **Ctrl** clave y arrastre el recurso para el segundo archivo. rc. Por ejemplo, arrastre **IDD_DIALOG1** desde `Source1.rc` a `Source2.rc`.

   > [!NOTE]
   > Arrastrar el recurso sin mantener presionada la **Ctrl** tecla mueve el recurso, en lugar de copiarlo.

## <a name="to-copy-resources-using-copy-and-paste"></a>Para copiar recursos con copiar y pegar

1. Abra ambos archivos de recursos independientes (para obtener más información, consulte [ver recursos en un archivo fuera de un proyecto de .rc](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md)). Por ejemplo, Source1.RF y Source2.rc.

1. En el archivo de origen desde el que desea copiar un recurso (por ejemplo, `Source1.rc`), haga clic en un recurso y elija **copia** en el menú contextual.

1. Haga clic en el archivo de recursos en la que desea pegar el recurso (por ejemplo, `Source2.rc`). Elija **pegar** en el menú contextual.

   > [!NOTE]
   > No se puede arrastrar y soltar, copiar, cortar o pegar entre archivos de recursos en el proyecto (**vista de recursos**) y archivos .rc independientes (aquellas abiertos en ventanas de documento). Podría hacerlo en las versiones anteriores del producto.

   > [!NOTE]
   > Para evitar conflictos con los nombres de símbolos o valores en el archivo existente, Visual C++ puede cambiar valor de símbolo del recurso transferido o nombre de símbolo y el valor cuando se copia al nuevo archivo.

## <a name="to-change-the-language-or-condition-of-a-resource-while-copying-c"></a>Para cambiar el idioma o la condición de un recurso al copiarlo (C++)

Al copiar un recurso, puede cambiar sus propiedades de idioma, condición o ambas.

- El idioma del recurso identifica exactamente eso, el idioma del recurso. Está usando el lenguaje [FindResource](/windows/desktop/api/winbase/nf-winbase-findresourcea) para ayudar a identificar el recurso que está buscando. (Sin embargo, los recursos pueden tener diferencias para cada idioma que no estén relacionados con texto, por ejemplo, se compila aceleradores que solo funcionen en teclados japoneses o un mapa de bits que solo sea adecuado para localizadas en chino).

- La condición de un recurso es un símbolo definido que identifica una condición en la que esta copia concreta del recurso se va a utilizar.

El idioma y la condición de un recurso se muestran entre paréntesis después del nombre del recurso en la ventana del área de trabajo. En este ejemplo, el recurso denominado IDD_AboutBox usa a finés como idioma y su condición es XX33.

```cpp
IDD_AboutBox (Finnish - XX33)
```

### <a name="to-copy-an-existing-resource-and-change-its-language-or-condition"></a>Para copiar un recurso existente y cambiar su idioma o su condición

1. En el archivo .rc o en la [vista de recursos](../windows/resource-view-window.md) ventana, haga clic en el recurso que van a copiar.

1. Elija **Insertar copia** en el menú contextual.

1. En el **Insertar copia de recursos** cuadro de diálogo:

   - Para el **lenguaje** cuadro de lista, seleccione el idioma.

   - En el **condición** , escriba la condición.

Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Resources in Desktop Apps](/dotnet/framework/resources/index) en el *Guía del desarrollador de .NET Framework*. Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, acceder a los recursos, mostrar recursos estáticos y asignar cadenas de recursos a propiedades, vea [crear archivos de recursos para las aplicaciones de escritorio](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Para obtener información sobre la globalización y localización de recursos en aplicaciones administradas, vea [Globalizar y localizar aplicaciones de .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Requisitos

Win32

## <a name="see-also"></a>Vea también

[Archivos de recursos](../windows/resource-files-visual-studio.md)<br/>
[Editores de recursos](../windows/resource-editors.md)<br/>
[Cómo: Abrir un archivo de script de recursos fuera de un proyecto (independiente)](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md)<br/>
