---
title: Edición en una tabla de aceleradores (C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- accelerator tables [C++], editing
- keyboard shortcuts [C++], editing in an accelerator table
ms.assetid: 545b650b-4f26-4b20-8431-d942548443bd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 57347b88fe7d54813e06cde6d5f4b3414e79f116
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46395815"
---
# <a name="editing-in-an-accelerator-table-c"></a>Edición en una tabla de aceleradores (C++)

### <a name="to-edit-in-an-accelerator-table"></a>Para editar el contenido de una tabla de aceleradores

1. Abra la tabla de aceleradores haciendo doble clic en el icono correspondiente en [vista de recursos](../windows/resource-view-window.md).

   > [!NOTE]
   > Si el proyecto no contuviera un archivo .rc, vea [Crear un nuevo archivo de script de recursos](../windows/how-to-create-a-resource-script-file.md).

2. Seleccione una entrada en la tabla y haga clic para activar la edición en contexto.

3. Seleccione en el cuadro combinado desplegable o escriba para realizar cambios.

   - Para [ID](id-property.md), seleccione en la lista o escriba para editar.

   - Para [modificador](../windows/accelerator-modifier-property.md), seleccione en la lista.

   - Para [clave](../windows/accelerator-key-property.md), seleccione en la lista o escriba para editar.

   - Para [tipo](../windows/accelerator-type-property.md), seleccione **ASCII** o **VIRTKEY** en la lista.

Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Resources in Desktop Apps](/dotnet/framework/resources/index) en el *Guía del desarrollador de .NET Framework*.

## <a name="requirements"></a>Requisitos

Win32

## <a name="see-also"></a>Vea también

[Edición de tablas de aceleradores](../windows/editing-accelerator-tables.md)<br/>
[Editor de aceleradores](../windows/accelerator-editor.md)