---
title: Cambiar o eliminar símbolos sin asignar
ms.date: 11/04/2016
f1_keywords:
- vc.editors.symbol.changing.unassigned
helpviewer_keywords:
- symbols [C++], unassigned
- Change Symbol dialog box [C++]
- unassigned symbols
- symbols [C++], deleting
ms.assetid: b6abee4a-3c24-4697-a166-fe6a86cad35f
ms.openlocfilehash: 47cc3d7a387092afe77fdbcf4bbdb6d085eeda25
ms.sourcegitcommit: 966e4466f10c93fc12faf33d28e03b39489423fc
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/11/2019
ms.locfileid: "55987019"
---
# <a name="changing-or-deleting-unassigned-symbols"></a>Cambiar o eliminar símbolos sin asignar

Mientras se encuentre en el [cuadro de diálogo símbolos de recursos](../windows/resource-symbols-dialog-box.md), puede editar o eliminar símbolos existentes que ya no están asignados a un recurso u objeto.

Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Resources in Desktop Apps](/dotnet/framework/resources/index) en el *Guía del desarrollador de .NET Framework*.

## <a name="to-change-an-unassigned-symbol"></a>Para cambiar un símbolo sin asignar

1. En el **nombre** cuadro, seleccione el símbolo sin asignar y elija **cambio**.

1. Editar nombre o un valor en los cuadros correspondientes en el símbolo del **cambiar símbolo** cuadro de diálogo.

   > [!NOTE]
   > Para cambiar un símbolo que *es* asignado a un recurso u objeto, debe usar el editor de recursos o **propiedades** ventana. Para obtener más información, consulte [cambiar un símbolo o el nombre](../windows/changing-a-symbol-or-symbol-name-id.md).

## <a name="to-delete-an-unassigned-unused-symbol"></a>Para eliminar un símbolo sin asignar (sin usar)

En el [cuadro de diálogo símbolos de recursos](../windows/resource-symbols-dialog-box.md), seleccione el símbolo que desea eliminar y elija **eliminar**.

   > [!NOTE]
   > Antes de eliminar un símbolo sin usar en un archivo de recursos, asegúrese de que no se usa en ninguna otra parte del programa o en archivos de recursos incluidos en el tiempo de compilación.

## <a name="requirements"></a>Requisitos

Win32

## <a name="see-also"></a>Vea también

[Visualización de símbolos de recursos](../windows/viewing-resource-symbols.md)<br/>
[Restricciones de los nombres de símbolo](../windows/symbol-name-restrictions.md)<br/>
[Restricciones de los valores de símbolo](../windows/symbol-value-restrictions.md)<br/>
[Identificadores de símbolo predefinidos](../windows/predefined-symbol-ids.md)