---
title: Interfaces del objeto de comando | Microsoft Docs
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
ms.openlocfilehash: 8176bad2921edd22edaab1688e38bc7de275b0bb
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2018
ms.locfileid: "50074805"
---
# <a name="command-object-interfaces"></a>Interfaces del objeto de comando

El objeto de comando utiliza el `IAccessor` interfaz para especificar enlaces de parámetros. El consumidor llama a `IAccessor::CreateAccessor`, pasa una matriz de `DBBINDING` estructuras. `DBBINDING` contiene información acerca de los enlaces de columna (por ejemplo, tipo y longitud). El proveedor recibe las estructuras y determina cómo se deben transferir los datos y si las conversiones son necesarias.

El `ICommandText` interfaz proporciona una manera de especificar un comando de texto. El `ICommandProperties` interfaz controla todas las propiedades de comando.

## <a name="see-also"></a>Vea también

[Arquitectura de plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)