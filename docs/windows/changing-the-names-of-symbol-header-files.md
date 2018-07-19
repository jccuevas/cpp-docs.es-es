---
title: Cambiar los nombres de archivos de encabezado de símbolos | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.symbol.changing.header
dev_langs:
- C++
helpviewer_keywords:
- resource files, multiple
- Resource Includes dialog box
- symbol header files, changing names
- symbol header files
- header files, changing names
- names [C++], symbol header files
- symbols, symbol header files
- Resource.h
ms.assetid: b948284a-7899-402e-ab12-9f2c8480ca9d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 953ac59958748bd58fa7e9027c595bf7905e5f27
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
ms.locfileid: "33864234"
---
# <a name="changing-the-names-of-symbol-header-files"></a>Cambiar los nombres de los archivos de encabezado de símbolos
Normalmente todas las definiciones de símbolos se guardan en Resource.h. Sin embargo, puede que necesite cambiar este nombre de archivo de inclusión para, por ejemplo, poder trabajar con más de un archivo de recursos en el mismo directorio.  
  
### <a name="to-change-the-name-of-the-resource-symbol-header-file"></a>Para cambiar el nombre del archivo de encabezado de símbolos de recurso  
  
1.  En [vista de recursos](../windows/resource-view-window.md), haga clic en el archivo .rc y elija [incluye recursos](../windows/resource-includes-dialog-box.md) en el menú contextual.  
  
    > [!NOTE]
    >  Si el proyecto no contuviera un archivo .rc, vea [Crear un nuevo archivo de script de recursos](../windows/how-to-create-a-resource-script-file.md).  
  
2.  En el **archivo de encabezado de símbolos** , escriba el nuevo nombre para el archivo de inclusión.  
  
 Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [recursos en aplicaciones de escritorio](/dotnet/framework/resources/index) en el *Guía del desarrollador de .NET Framework.*  
  
 Requisitos  
  
 Win32  
  
## <a name="see-also"></a>Vea también  
 [Ver símbolos de recursos](../windows/viewing-resource-symbols.md)   
 [Identificadores de símbolo predefinidos](../windows/predefined-symbol-ids.md)