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
ms.openlocfilehash: 436c796b24b0fa498f2b3f45e848392635b22a34
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376037"
---
# <a name="using-stored-procedures"></a>Utilizar procedimientos almacenados

Un procedimiento almacenado es un objeto ejecutable almacenado en una base de datos. Llamar a un procedimiento almacenado es similar a invocar un comando SQL. El uso de procedimientos almacenados en el origen de datos (en lugar de ejecutar o preparar una instrucción en la aplicación cliente) puede proporcionar varias ventajas, incluido un mayor rendimiento, una reducción de la sobrecarga de red y una mayor coherencia y precisión.

Un procedimiento almacenado puede tener cualquier número de parámetros de entrada o salida (incluido cero) y puede pasar un valor devuelto. Puede codificar valores de parámetros como valores de datos específicos o utilizar un marcador de parámetro (un signo de interrogación '?').

> [!NOTE]
> Los procedimientos almacenados de SQL Server de CLR `/clr:safe` creados con Visual C++ deben compilarse con la opción del compilador.

El proveedor OLE DB para SQL Server (SQLOLEDB) admite los siguientes mecanismos que los procedimientos almacenados usan para devolver datos:

- Cada instrucción **SELECT** del procedimiento genera un conjunto de resultados.

- El procedimiento puede devolver datos mediante parámetros de salida.

- El procedimiento puede tener un código de retorno de tipo entero.

> [!NOTE]
> No puede usar procedimientos almacenados con el proveedor OLE DB para Jet porque ese proveedor no admite procedimientos almacenados; solo se permiten constantes en las cadenas de consulta.

## <a name="see-also"></a>Consulte también

[Trabajar con plantillas de consumidor OLE DB](../../data/oledb/working-with-ole-db-consumer-templates.md)
