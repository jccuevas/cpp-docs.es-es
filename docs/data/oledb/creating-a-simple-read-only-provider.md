---
title: Crear un proveedor sencillo de sólo lectura | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- OLE DB providers, creating
- OLE DB provider templates, creating providers
ms.assetid: ade8ccdd-9ea4-4e46-a964-18460c2a2401
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 9f951fba45b23b7e4dde92fc11f2faabb53bd43d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46101571"
---
# <a name="creating-a-simple-read-only-provider"></a>Crear un proveedor sencillo de sólo lectura

Cuando haya creado un proveedor OLE DB mediante el Asistente para proyectos ATL y el Asistente para proveedores OLE DB ATL, puede agregar otras funcionalidades que desea admitir. Empezar a diseñar su proveedor examinando el tipo de datos que se va a enviar al consumidor y bajo qué condiciones. Es especialmente importante determinar si necesita admitir los comandos, transacciones y otros objetos opcionales. Un buen diseño por adelantado acelerará la implementación y pruebas.  
  
En el ejemplo se presenta en dos partes:  
  
- La primera parte se muestra cómo [crear un proveedor sencillo de sólo lectura](../../data/oledb/implementing-the-simple-read-only-provider.md) que lee un par de cadenas.  
  
- La segunda parte muestra cómo [mejorar un proveedor sencillo de sólo lectura](../../data/oledb/enhancing-the-simple-read-only-provider.md) agregando el `IRowsetLocate` interfaz.  
  
## <a name="see-also"></a>Vea también  

[Crear un proveedor OLE DB](../../data/oledb/creating-an-ole-db-provider.md)