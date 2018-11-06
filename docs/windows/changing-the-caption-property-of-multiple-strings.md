---
title: Cambiar la propiedad Caption de varios recursos de cadena (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- String editor [C++], changing properties of multiple strings
- string tables [C++], changing caption of multiple strings
ms.assetid: 82ac4389-fd9c-4794-a18f-c6bf5b253bd7
ms.openlocfilehash: a0b658684a948bd006c392188ed650756bda297d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50530837"
---
# <a name="changing-the-caption-property-of-multiple-string-resources-c"></a>Cambiar la propiedad Caption de varios recursos de cadena (C++)

El siguiente procedimiento muestra cómo cambiar la propiedad caption de varias cadenas.

### <a name="to-change-the-caption-property-of-multiple-strings"></a>Para cambiar la propiedad caption de varias cadenas

1. Abra la tabla de cadenas haciendo doble clic en el icono correspondiente en [vista de recursos](../windows/resource-view-window.md).

   > [!NOTE]
   > Si el proyecto no contuviera un archivo .rc, vea [Crear un nuevo archivo de script de recursos](../windows/how-to-create-a-resource-script-file.md).

2. Seleccione las cadenas que desee cambiar, mantenga presionada la **Ctrl** clave al hacer clic en cada uno de ellos.

3. En el [ventana propiedades](/visualstudio/ide/reference/properties-window), escriba un nuevo valor para la propiedad que desee cambiar.

4. Presione **ENTRAR**.

Para obtener información sobre cómo agregar recursos a proyectos administrados (aquellos que tienen como destino common language runtime), consulte [Resources in Desktop Apps](/dotnet/framework/resources/index) en el *Guía del desarrollador de .NET Framework*. Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, acceder a los recursos, mostrar recursos estáticos y asignar cadenas de recursos a propiedades, vea [Tutorial: adaptar Windows Forms](/previous-versions/visualstudio/visual-studio-2010/y99d1cd3).

## <a name="requirements"></a>Requisitos

Win32

## <a name="see-also"></a>Vea también

[Editor de cadenas](../windows/string-editor.md)