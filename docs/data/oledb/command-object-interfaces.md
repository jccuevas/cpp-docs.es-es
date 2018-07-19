---
title: Interfaces del objeto de comando | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- command object interfaces [C++]
- command objects [OLE DB]
- OLE DB [C++], command object interfaces
ms.assetid: dacff5ae-252c-4f20-9ad7-4e602cc48536
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 9c597cc30e23ffce2787eac6c13f6ba8c53f96c1
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33096124"
---
# <a name="command-object-interfaces"></a>Interfaces del objeto de comando
El objeto de comando utiliza el `IAccessor` interfaz para especificar enlaces de parámetros. El consumidor llama `IAccessor::CreateAccessor`, pasando una matriz de `DBBINDING` estructuras. `DBBINDING` contiene información acerca de los enlaces de columna (por ejemplo, tipo y longitud). El proveedor recibe las estructuras y determina cómo se deben transferir los datos y si las conversiones son necesarias.  
  
 El `ICommandText` interfaz proporciona una manera de especificar un comando de texto. El `ICommandProperties` interfaz controla todas las propiedades de comando.  
  
## <a name="see-also"></a>Vea también  
 [Arquitectura de plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)