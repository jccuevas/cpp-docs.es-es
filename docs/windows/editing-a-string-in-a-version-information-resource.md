---
title: Editar una cadena en un recurso de información de versión | Documentos de Microsoft
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
- version information resources
- resources [Visual Studio], editing version information
ms.assetid: d3a7d4e4-7d31-47c2-902c-f50b8404ba4f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 80795f912ab41809b19e77bd33f56243541d4de1
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
---
# <a name="editing-a-string-in-a-version-information-resource"></a>Editar una cadena en un recurso de información de versión
### <a name="to-edit-a-string-in-a-version-information-resource"></a>Para editar una cadena en un recurso de información de versión  
  
1.  Haga clic en el elemento una vez para seleccionarlo y luego comience a editarlo. Realice los cambios directamente en la tabla Información de versión o en la [ventana Propiedades](/visualstudio/ide/reference/properties-window). Los cambios que realice se reflejarán en ambos lugares.  
  
     **Nota** Al editar la clave **FILEFLAGS** en el editor de la Información de versión, observará que no puede establecer la propiedades **Depuración**, **Compilación privada**o **Compilación especial** (en la ventana Propiedades) para archivos .rc:  
  
    -   El editor Información de versión establece la propiedad **Depuración** con #ifdef en el script de recursos, según la marca de compilación **_DEBUG** .  
  
    -   Si la clave **Compilación privada** tiene un **Valor** establecido en la tabla Información de versión, la propiedad **Compilación privada** correspondiente (en la ventana Propiedades) de la clave **FILEFLAGS** será **True**. Si el **Valor** está vacío, la propiedad será **False**. Del mismo modo, la clave **Compilación especial** (en la tabla Información de versión) está vinculada a la propiedad **Compilación especial** para la clave **FILEFLAGS** .  
  
 Para ordenar la secuencia de información del bloque de cadenas, haga clic en los encabezados de columna Clave o Valor. Estos encabezados reorganizan automáticamente la información en la secuencia seleccionada.  
  
 Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [recursos en aplicaciones de escritorio](/dotnet/framework/resources/index) en el *Guía del desarrollador de .NET Framework.* Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, tener acceso a recursos, mostrar recursos estáticos y asignar cadenas de recursos a propiedades, vea [crear archivos de recursos para las aplicaciones de escritorio](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Para obtener información sobre la globalización y localización de recursos en aplicaciones administradas, vea [Globalizar y localizar aplicaciones de .NET Framework](/dotnet/standard/globalization-localization/index).  
  
 **Requisitos**  
  
 Win32  
  
## <a name="see-also"></a>Vea también  
 [Editor de información de versión](../windows/version-information-editor.md)   
 [Información de versión (Windows)](https://msdn.microsoft.com/library/windows/desktop/ms646981.aspx)

