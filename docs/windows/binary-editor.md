---
title: Editor binario (C++)
ms.date: 11/04/2016
f1_keywords:
- vc.editors.binary.F1
helpviewer_keywords:
- editors, Binary
- resources [C++], editing
- resource editors [C++], Binary editor
- Binary editor
ms.assetid: 2483c48b-1252-4dbc-826b-82e6c1a0e9cb
ms.openlocfilehash: 1b5e1c16ff63c55617ee9b2bbcb47a7201635789
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50451706"
---
# <a name="binary-editor-c"></a>Editor binario (C++)

> [!WARNING]
> El **Editor binario** no está disponible en las ediciones Express.

El Editor binario permite editar cualquier recurso, a nivel binario, en formato ASCII o hexadecimal. También se puede utilizar el [comando Buscar](/visualstudio/ide/reference/find-command) para buscar cadenas ASCII o bytes hexadecimales. Debe usar el **binario** editor solo cuando necesite ver o realizar menores cambia a los recursos personalizados o tipos de recursos no admitidos en el entorno de Visual Studio.

Para abrir el **Editor binario**, primero elija **archivo** > **New** > **archivo** desde el menú principal, seleccione el archivo que desea editar y, después, haga clic en la flecha desplegable situada junto a la **abierto** botón y elija **abrir con** > **Editor binario**.

> [!CAUTION]
> Es peligroso editar recursos como cuadros de diálogo, imágenes o menús en el Editor binario. Una edición incorrecta podría dañar el recurso y hacerlo ilegible en su editor nativo.

> [!TIP]
> Al usar el **binario** editor, en muchos casos, hacer clic en para mostrar un menú contextual de comandos específicos del recurso. Los comandos disponibles dependen del objeto al que apunta el cursor. Por ejemplo, si hace clic mientras señala a la **binario** editor teniendo seleccionados valores hexadecimales, el menú contextual muestra los **cortar**, **copia**, y **pegar**  comandos.

Con el **binario** editor, puede:

- [Abrir un recurso para editarlo en modo binario](../windows/opening-a-resource-for-binary-editing.md)

- [Editar datos binarios](../windows/editing-binary-data.md)

- [Buscar datos binarios](../windows/finding-binary-data.md)

- [Crear un nuevo recurso personalizado o de datos](../windows/creating-a-new-custom-or-data-resource.md)

## <a name="managed-resources"></a>Recursos administrados

Puede usar el [editor de imágenes](../windows/image-editor-for-icons.md) y **binario** editor para trabajar con archivos de recursos en proyectos administrados. Todos los recursos administrados que vaya a editar deberán estar vinculados. Los editores de recursos de Visual Studio no admiten la edición de recursos incrustados.

Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Resources in Desktop Apps](/dotnet/framework/resources/index) en el *Guía del desarrollador de .NET Framework*. Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, acceder a los recursos, mostrar recursos estáticos y asignar cadenas de recursos a propiedades, vea [crear archivos de recursos para las aplicaciones de escritorio](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Para obtener información sobre la globalización y localización de recursos en aplicaciones administradas, vea [Globalizar y localizar aplicaciones de .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Requisitos

Ninguna

## <a name="see-also"></a>Vea también

[Editores de recursos](../windows/resource-editors.md)