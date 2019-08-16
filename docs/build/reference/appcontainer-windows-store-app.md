---
title: /APPCONTAINER (aplicación de UWP/Microsoft Store)
ms.date: 11/04/2016
ms.assetid: 9a432db5-7640-460b-ab18-6f61fa7daf6f
ms.openlocfilehash: f7ab8cf1ce034580953fdf1403264e8ef3d3ff09
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62295128"
---
# <a name="appcontainer-microsoft-store-app"></a>/APPCONTAINER (aplicación de Microsoft Store)

Especifica si el vinculador crea una imagen ejecutable que se debe ejecutar en un contenedor de aplicaciones.

## <a name="syntax"></a>Sintaxis

```
/APPCONTAINER[:NO]
```

## <a name="remarks"></a>Comentarios

De forma predeterminada, /APPCONTAINER está desactivado.

Esta opción modifica un archivo ejecutable para indicar si se debe ejecutar la aplicación en el entorno de aislamiento de proceso appcontainer. Especifique /APPCONTAINER para una aplicación que se debe ejecutar en el entorno de appcontainer, por ejemplo, una aplicación de 8.x plataforma Universal de Windows (UWP) o Windows Phone. (La opción se establece automáticamente en Visual Studio cuando se crea una aplicación Windows Universal desde una plantilla.) Para una aplicación de escritorio, especifique/appcontainer: no o simplemente omita la opción.

La opción /APPCONTAINER se introdujo en Windows 8.

### <a name="to-set-this-linker-option-in-visual-studio"></a>Para establecer esta opción del vinculador en Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [propiedades de compilación y el compilador de C++ establece en Visual Studio](../working-with-project-properties.md).

1. Expanda el nodo **Propiedades de configuración**.

1. Expanda el **vinculador** nodo.

1. Seleccione el **línea de comandos** página de propiedades.

1. En **opciones adicionales**, escriba `/APPCONTAINER` o `/APPCONTAINER:NO`.

## <a name="see-also"></a>Vea también

[Referencia del enlazador MSVC](linking.md)<br/>
[Opciones del enlazador MSVC](linker-options.md)
