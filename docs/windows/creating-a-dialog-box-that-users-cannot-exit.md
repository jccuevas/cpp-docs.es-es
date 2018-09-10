---
title: Creación de un cuadro de diálogo (C++) que los usuarios no puedan salir | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- dialog boxes [C++], creating
- modal dialog boxes [C++], logon screens
- logon screens
ms.assetid: 54823c27-1658-4388-bd12-0a1ce8f3899e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: f0b9c290cb8e5ced7537fb377d6e7ac52f20d089
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/10/2018
ms.locfileid: "44314552"
---
# <a name="creating-a-dialog-box-c-that-users-cannot-exit"></a>Creación de un cuadro de diálogo (C++) que los usuarios no puedan salir

Puede crear un cuadro de diálogo en tiempo de ejecución del que un usuario no pueda salir. Este tipo de cuadro de diálogo es útil para inicios de sesión y para bloqueos de documentos o aplicaciones.

### <a name="to-create-a-dialog-box-that-a-user-cannot-exit"></a>Par crear un cuadro de diálogo del que un usuario no pueda salir.

1. En el panel **Propiedades** para el cuadro de diálogo, establezca la propiedad **Menú del sistema** en **false**.

   Esto deshabilita el menú del sistema del cuadro de diálogo y el botón **Cerrar** .

2. En el formulario del cuadro de diálogo, elimine los botones **Cancelar** y **Aceptar** .

   En tiempo de ejecución, un usuario no puede salir de un cuadro de diálogo modal que tenga estas características.

Para habilitar la comprobación de este tipo de cuadro de diálogo, la función de cuadro de diálogo de prueba detecta cuando **Esc** está presionado. (**Esc** es también conocida como tecla virtual VK_ESCAPE.) Independientemente de cómo el cuadro de diálogo está diseñado para comportarse en tiempo de ejecución, puede finalizarlo en modo de prueba presionando **Esc**.

> [!NOTE]
> Para aplicaciones MFC, para crear un cuadro de diálogo que los usuarios no puedan salir, debe invalidar el comportamiento predeterminado de `OnOK` y `OnCancel` porque si elimina los botones asociados, todavía se puede descartar el cuadro de diálogo presionando  **Escriba** o **Esc**.

Para obtener información acerca de cómo agregar recursos a proyectos administrados, vea [Resources in Desktop Apps](/dotnet/framework/resources/index).

## <a name="requirements"></a>Requisitos

Win32

## <a name="see-also"></a>Vea también

[Procedimiento para crear un recurso](../windows/how-to-create-a-resource.md)  
[Archivos de recursos](../windows/resource-files-visual-studio.md)  
[Editor de cuadros de diálogo](../windows/dialog-editor.md)