---
title: Usar procedimientos almacenados
ms.date: 10/24/2018
helpviewer_keywords:
- OLE DB, stored procedures
- stored procedures, Visual C++
- stored procedures, about stored procedures
- OLE DB provider templates, stored procedures
- stored procedures, OLE DB
ms.assetid: 90507e4c-eca2-46c9-ad8c-07e10dc1d41b
ms.openlocfilehash: a7e97781d245e236c57942db15d61080d6418cfa
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80209279"
---
# <a name="using-stored-procedures"></a>Usar procedimientos almacenados

Un procedimiento almacenado es un objeto ejecutable almacenado en una base de datos. Llamar a un procedimiento almacenado es similar a invocar un comando SQL. El uso de procedimientos almacenados en el origen de datos (en lugar de ejecutar o preparar una instrucción en la aplicación cliente) puede proporcionar varias ventajas, entre las que se incluyen un rendimiento mayor, una sobrecarga de red reducida y una mayor coherencia y precisión.

Un procedimiento almacenado puede tener cualquier número de parámetros de entrada o salida (incluido cero) y puede pasar un valor devuelto. Puede codificar los valores de los parámetros como valores de datos específicos o usar un marcador de parámetros (un signo de interrogación '? ').

> [!NOTE]
>  CLR SQL Server procedimientos almacenados creados con Visual C++ se debe compilar con la opción del compilador `/clr:safe`.

El proveedor de OLE DB para SQL Server (SQLOLEDB) admite los siguientes mecanismos que los procedimientos almacenados usan para devolver datos:

- Cada instrucción **Select** del procedimiento genera un conjunto de resultados.

- El procedimiento puede devolver datos mediante parámetros de salida.

- El procedimiento puede tener un código de retorno de tipo entero.

> [!NOTE]
> No puede utilizar procedimientos almacenados con el proveedor de OLE DB para Jet porque ese proveedor no admite procedimientos almacenados; solo se permiten constantes en las cadenas de consulta.

## <a name="see-also"></a>Consulte también

[Trabajar con plantillas de consumidor OLE DB](../../data/oledb/working-with-ole-db-consumer-templates.md)
