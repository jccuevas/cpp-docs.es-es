---
title: Uso de procedimientos almacenados | Microsoft Docs
ms.custom: ''
ms.date: 10/24/2018
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- OLE DB, stored procedures
- stored procedures, Visual C++
- stored procedures, about stored procedures
- OLE DB provider templates, stored procedures
- stored procedures, OLE DB
ms.assetid: 90507e4c-eca2-46c9-ad8c-07e10dc1d41b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 062384713e0668965f9d04dc8f6907b05ac2bc89
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2018
ms.locfileid: "50076885"
---
# <a name="using-stored-procedures"></a>Utilizar procedimientos almacenados

Un procedimiento almacenado es un objeto ejecutable almacenado en una base de datos. Llamar a un procedimiento almacenado es similar a invocar un comando SQL. Usar procedimientos almacenados en el origen de datos (en lugar de ejecutar o preparar una instrucción en la aplicación cliente) puede proporcionar varias ventajas, incluido un mayor rendimiento, tráfico de red reducido y coherencia mejorada y la precisión.

Un procedimiento almacenado puede tener cualquier número de (incluido el cero) entrada o parámetros de salida y puede pasar un valor devuelto. Puede crear los valores de parámetro codificar de forma rígida como valores de datos específicas o usar un marcador de parámetro (un signo de interrogación '?').

> [!NOTE]
>  CLR de SQL Server se deben compilar los procedimientos almacenados creados mediante Visual C++ con el `/clr:safe` opción del compilador.

El proveedor OLE DB para SQL Server (SQLOLEDB) admite los siguientes mecanismos que se usan para devolver datos de los procedimientos almacenan:

- Cada **seleccione** instrucción del procedimiento genera un conjunto de resultados.

- El procedimiento puede devolver datos a través de los parámetros de salida.

- El procedimiento puede tener un número entero de código de retorno.

> [!NOTE]
> No se puede utilizar procedimientos almacenados con el proveedor OLE DB para Jet porque ese proveedor no admite procedimientos almacenados; solo se permiten constantes en las cadenas de consulta.

## <a name="see-also"></a>Vea también

[Trabajar con plantillas de consumidor OLE DB](../../data/oledb/working-with-ole-db-consumer-templates.md)