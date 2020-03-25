---
title: Identificadores de símbolo predefinidos
ms.date: 02/14/2019
helpviewer_keywords:
- symbols [C++], predefined IDs
- predefined symbol IDs
ms.assetid: 91a5d610-1a04-47e8-b8a4-63ad650a90df
ms.openlocfilehash: 8f7fcba864f4e1a47d217d684b87c257503aeb13
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80215168"
---
# <a name="predefined-symbol-ids"></a>Identificadores de símbolo predefinidos

Cuando se inicia un proyecto nuevo, dependiendo del tipo de proyecto, es posible que se hayan predefinido algunos identificadores de símbolo. Estos identificadores son compatibles con los distintos tipos de proyectos y bibliotecas (por ejemplo, MFC). Representan tareas comunes que se suelen incluir en todas las aplicaciones, o acciones de elementos de hardware, como un mouse o una impresora.

Estos identificadores de símbolo son importantes al trabajar con recursos. Están disponibles cuando se editan tablas de aceleradores y algunas de ellas ya están asociadas a las claves virtuales. También están disponibles a través del [ventana Propiedades](/visualstudio/ide/reference/properties-window). Puede asignar cualquiera de los identificadores de símbolo predefinidos a los nuevos recursos, o puede asignarles teclas de aceleración y la funcionalidad asociada con el identificador de símbolo se asocia automáticamente a esa combinación de teclas.

Las bibliotecas tienen símbolos predefinidos que aparecerán como parte del proyecto:

- [Símbolos predefinidos de ATL](../windows/atl-predefined-symbols.md)

- [Símbolos predefinidos de MFC](../windows/mfc-predefined-symbols.md)

- [Símbolos predefinidos de Win32](../windows/win32-predefined-symbols.md)

> [!NOTE]
> Los símbolos predefinidos son siempre de solo lectura.

## <a name="requirements"></a>Requisitos

Win32, MFC o ATL

## <a name="see-also"></a>Consulte también

[Identificadores de recursos (símbolos)](../windows/symbols-resource-identifiers.md)<br/>
[Cómo: crear símbolos](../windows/creating-new-symbols.md)<br/>
[Cómo: administrar símbolos](../windows/changing-a-symbol-or-symbol-name-id.md)<br/>
