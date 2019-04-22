---
title: Utilizar procedimientos almacenados
ms.date: 10/24/2018
helpviewer_keywords:
- OLE DB, stored procedures
- stored procedures, Visual C++
- stored procedures, about stored procedures
- OLE DB provider templates, stored procedures
- stored procedures, OLE DB
ms.assetid: 90507e4c-eca2-46c9-ad8c-07e10dc1d41b
ms.openlocfilehash: 7ace43283c56c0c859b193f63e8ca104f6b52a31
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59041181"
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