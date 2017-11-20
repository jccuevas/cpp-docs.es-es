---
title: Interfaces del objeto de comando | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- command object interfaces [C++]
- command objects [OLE DB]
- OLE DB [C++], command object interfaces
ms.assetid: dacff5ae-252c-4f20-9ad7-4e602cc48536
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 734018229eff0db3a1ed1a779be39e59b75447f8
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="command-object-interfaces"></a>Interfaces del objeto de comando
El objeto de comando utiliza el `IAccessor` interfaz para especificar enlaces de parámetros. El consumidor llama `IAccessor::CreateAccessor`, pasando una matriz de `DBBINDING` estructuras. `DBBINDING`contiene información acerca de los enlaces de columna (por ejemplo, tipo y longitud). El proveedor recibe las estructuras y determina cómo se deben transferir los datos y si las conversiones son necesarias.  
  
 El `ICommandText` interfaz proporciona una manera de especificar un comando de texto. El `ICommandProperties` interfaz controla todas las propiedades de comando.  
  
## <a name="see-also"></a>Vea también  
 [Arquitectura de plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)