---
title: Editar una cadena en un recurso de información de versión (C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.version
dev_langs:
- C++
helpviewer_keywords:
- version information resources [C++]
- resources [C++], editing version information
ms.assetid: d3a7d4e4-7d31-47c2-902c-f50b8404ba4f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c5cc7da4629ba00bbb1c48d764b836897c0b3748
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/10/2018
ms.locfileid: "44316983"
---
# <a name="editing-a-string-in-a-version-information-resource-c"></a>Editar una cadena en un recurso de información de versión (C++)

### <a name="to-edit-a-string-in-a-version-information-resource"></a>Para editar una cadena en un recurso de información de versión

1. Haga clic en el elemento una vez para seleccionarlo y luego comience a editarlo. Realice los cambios directamente en el **información de versión** tabla o en el [ventana propiedades](/visualstudio/ide/reference/properties-window). Los cambios que realice se reflejarán en ambos lugares.

   > [!NOTE] 
   > Cuando se edita la `FILEFLAGS` clave en el **información de versión** editor, observará que no se puede establecer el **depurar**, **compilación privada**, o **especiales Compilar** propiedades (en el **propiedades** ventana) para archivos. rc:

   - El **información de versión** editor establece la **depurar** propiedad con un `#ifdef` en el script de recursos, según la `_DEBUG` marca de compilación.

   - Si el `Private Build` clave tiene un **valor** establecido el **información de versión** de tabla, la correspondiente **compilación privada** propiedad (en el **propiedades**  ventana) para el `FILEFLAGS` clave será **True**. Si el **Valor** está vacío, la propiedad será **False**. Del mismo modo, el **Special Build** clave (en el **información de versión** tabla) está asociado a la **Special Build** propiedad para el `FILEFLAGS` clave.

Para ordenar la secuencia de información del bloque de cadenas, haga clic en los encabezados de columna Clave o Valor. Estos encabezados reorganizan automáticamente la información en la secuencia seleccionada.

Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Resources in Desktop Apps](/dotnet/framework/resources/index) en el *Guía del desarrollador de .NET Framework*. Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, acceder a los recursos, mostrar recursos estáticos y asignar cadenas de recursos a propiedades, vea [crear archivos de recursos para las aplicaciones de escritorio](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Para obtener información sobre la globalización y localización de recursos en aplicaciones administradas, vea [Globalizar y localizar aplicaciones de .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Requisitos

Win32

## <a name="see-also"></a>Vea también

[Editor de la información de versión](../windows/version-information-editor.md)  
[Información de versión (Windows)](https://msdn.microsoft.com/library/windows/desktop/ms646981.aspx)