---
title: Identificadores de símbolo predefinidos
ms.date: 02/14/2019
helpviewer_keywords:
- symbols [C++], predefined IDs
- predefined symbol IDs
ms.assetid: 91a5d610-1a04-47e8-b8a4-63ad650a90df
ms.openlocfilehash: d7402bf7aaaf7c72382b57963d5d759adaa71115
ms.sourcegitcommit: 470de1337035dd33682d935b4b6c6d8b1bdb0bbb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/15/2019
ms.locfileid: "56320801"
---
# <a name="predefined-symbol-ids"></a>Identificadores de símbolo predefinidos

Cuando se inicia un proyecto nuevo, dependiendo del tipo de proyecto, es posible que se hayan predefinido algunos identificadores de símbolo. Estos identificadores son compatibles con los distintos tipos de proyectos y bibliotecas (por ejemplo, MFC). Representan tareas comunes que se suelen incluir en todas las aplicaciones, o acciones de elementos de hardware, como un mouse o una impresora.

Estos identificadores de símbolo son importantes al trabajar con recursos. Se encuentran disponibles al editar tablas de aceleradores y algunos de ellos ya están asociados con teclas virtuales. También están disponibles a través del [ventana propiedades](/visualstudio/ide/reference/properties-window). Puede asignar cualquiera de los identificadores de símbolo predefinidos a los nuevos recursos, o también puede asignar a estos identificadores teclas de aceleración. En este caso, la funcionalidad asociada con el identificador de símbolo se asociará a su vez de forma automática con la combinación de teclas en cuestión.

Estas bibliotecas cuentan con símbolos predefinidos que aparecerán como parte del proyecto:

- [Símbolos predefinidos de MFC](../windows/mfc-predefined-symbols.md)

- [Símbolos predefinidos de ATL](../windows/atl-predefined-symbols.md)

- [Símbolos predefinidos de Win32](../windows/win32-predefined-symbols.md)

   > [!NOTE]
   > Los símbolos predefinidos son siempre de solo lectura.

## <a name="requirements"></a>Requisitos

Win32, MFC o ATL

## <a name="see-also"></a>Vea también

[Identificadores de recursos (símbolos)](../windows/symbols-resource-identifiers.md)<br/>
[Creación de símbolos](../windows/creating-new-symbols.md)<br/>
[Administrar los símbolos](../windows/changing-a-symbol-or-symbol-name-id.md)<br/>