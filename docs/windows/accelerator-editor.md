---
title: Editor de aceleradores | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.accelerator.F1
dev_langs:
- C++
helpviewer_keywords:
- accelerator tables [C++], editing
- tables [Visual Studio], accelerator key
- accelerator keys
- resource editors, Accelerator editor
- keyboard shortcuts [C++], Accelerator editor
- Accelerator editor
ms.assetid: 013c30b6-5d61-4f1c-acef-8bd15bed7060
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 0e5ce1fcd71f6f49532d083c7cb2dcfce9ed644c
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
---
# <a name="accelerator-editor"></a>Editor de aceleradores
Una tabla de aceleradores es un recurso de Windows que contiene una lista de teclas de aceleración (también conocidas como teclas de método abreviado) y los identificadores de comandos asociados con ellas. Un programa puede tener más de una tabla de aceleradores.  
  
 Normalmente, los aceleradores se usan como métodos abreviados de teclado para comandos de programa que también están disponibles en un menú o una barra de herramientas. Sin embargo, puede usar la tabla de aceleradores para definir las combinaciones de teclas para los comandos que no tienen asociado un objeto de interfaz de usuario.  
  
 Puede usar la [Vista de clases](http://msdn.microsoft.com/en-us/8d7430a9-3e33-454c-a9e1-a85e3d2db925) para enlazar comandos de teclas de aceleración al código.  
  
 Con el editor de aceleradores, puede:  
  
-   [Establecer propiedades de acelerador](../windows/setting-accelerator-properties.md)  
  
-   [Asociar una tecla de aceleración a un elemento de menú](../windows/associating-an-accelerator-key-with-a-menu-item.md)  
  
-   [Editar tablas de aceleradores](../windows/editing-accelerator-tables.md)  
  
-   [Usar teclas de aceleración predefinidas](../windows/predefined-accelerator-keys.md)  
  
    > [!TIP]
    >  Al usar el Editor de aceleradores, puede hacer clic con el botón secundario para mostrar un menú contextual de los comandos usados con mayor frecuencia. Los comandos disponibles dependen del objeto al que apunta el puntero.  
  
    > [!NOTE]
    >  Windows no permite crear tablas de aceleradores vacías. Si crea una tabla de aceleradores sin entradas, se elimina automáticamente al guardar la tabla.  
  
 Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [recursos en aplicaciones de escritorio](/dotnet/framework/resources/index) en el *Guía del desarrollador de .NET Framework.* Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, tener acceso a recursos, mostrar recursos estáticos y asignar cadenas de recursos a propiedades, vea [crear archivos de recursos para las aplicaciones de escritorio](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Para obtener información sobre la globalización y localización de recursos en aplicaciones administradas, vea [Globalizar y localizar aplicaciones de .NET Framework](/dotnet/standard/globalization-localization/index).  
  
## <a name="requirements"></a>Requisitos  
 Win32  
  
## <a name="see-also"></a>Vea también  
 [Editores de recursos](../windows/resource-editors.md)

