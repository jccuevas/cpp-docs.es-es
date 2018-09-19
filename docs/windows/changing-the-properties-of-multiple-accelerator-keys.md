---
title: Cambiar las propiedades de varias teclas de aceleración (C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- keyboard shortcuts [C++], property changing
- accelerator tables [C++], changing properties
ms.assetid: b55c9bd6-b430-48bb-b942-0e6f21d7abf9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: bf70622dc901842a74cf8718d9447f899defb57d
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/10/2018
ms.locfileid: "44313525"
---
# <a name="changing-the-properties-of-multiple-accelerator-keys-c"></a>Cambiar las propiedades de varias teclas de aceleración (C++)

### <a name="to-change-the-properties-of-multiple-accelerator-keys"></a>Para cambiar las propiedades de varias teclas de aceleración

1. Abra la tabla de aceleradores haciendo doble clic en el icono correspondiente en [vista de recursos](../windows/resource-view-window.md).

   > [!NOTE]
   > Si el proyecto no contuviera un archivo .rc, vea [Crear un nuevo archivo de script de recursos](../windows/how-to-create-a-resource-script-file.md).

2. Seleccione las teclas de aceleración que desee cambiar, mantenga presionada la **Ctrl** clave al hacer clic en cada uno de ellos.

3. Vaya a la [ventana propiedades](/visualstudio/ide/reference/properties-window) y escriba los valores que desea que todos los aceleradores seleccionados para compartir.

   > [!NOTE]
   > Cada valor de modificador aparece como una propiedad booleana en el **propiedades** ventana. Si cambia un [modificador](../windows/accelerator-modifier-property.md) valor en el **propiedades** ventana, la tabla de aceleradores tratará al nuevo modificador como una adición a los modificadores que previamente contenía. Por este motivo, si establece los valores de modificador, deberá establecer todos ellos para asegurarse de que todos los aceleradores compartan la misma **modificador** configuración.

Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Resources in Desktop Apps](/dotnet/framework/resources/index) en el *Guía del desarrollador de .NET Framework*. Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, acceder a los recursos, mostrar recursos estáticos y asignar cadenas de recursos a propiedades, vea [crear archivos de recursos para las aplicaciones de escritorio](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Para obtener información sobre la globalización y localización de recursos en aplicaciones administradas, vea [Globalizar y localizar aplicaciones de .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Requisitos

Win32

## <a name="see-also"></a>Vea también

[Edición de tablas de aceleradores](../windows/editing-accelerator-tables.md)  
[Editor de aceleradores](../windows/accelerator-editor.md)