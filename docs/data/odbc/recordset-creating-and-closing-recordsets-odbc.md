---
title: 'Conjunto de registros: Crear y cerrar conjuntos de registros (ODBC)'
ms.date: 11/04/2016
helpviewer_keywords:
- ODBC recordsets, creating
- recordsets, creating
- recordsets, opening
- recordsets, closing
- ODBC recordsets, closing
- ODBC recordsets, opening
ms.assetid: 8d2aac23-4396-4ce2-8c60-5ecf1b360d3d
ms.openlocfilehash: d98f7e59e52b86a1b9b1c3ffac5c3e7160e6c36d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50581511"
---
# <a name="recordset-creating-and-closing-recordsets-odbc"></a>Conjunto de registros: Crear y cerrar conjuntos de registros (ODBC)

Este tema es aplicable a las clases ODBC de MFC.

Para usar un conjunto de registros, construya un objeto de conjunto de registros y, a continuación, llame a su `Open` función miembro para ejecutar la consulta y seleccionar los registros. Cuando termine con el conjunto de registros, cerrar y destruir el objeto.

En este tema se explica:

- [Cuándo y cómo crear un objeto recordset](#_core_creating_recordsets_at_run_time).

- [Cuándo y cómo puede calificar el comportamiento del conjunto de registros mediante la parametrización, filtrado, ordenación o bloquearla](#_core_setting_recordset_options).

- [Cuándo y cómo cerrar un objeto recordset](#_core_closing_a_recordset).

##  <a name="_core_creating_recordsets_at_run_time"></a> Creación de conjuntos de registros en tiempo de ejecución

Antes de poder crear objetos de conjunto de registros en el programa, normalmente se escriben las clases de conjunto de registros específicos de la aplicación. Para obtener más información sobre este paso preliminar, consulte [agregar un consumidor ODBC de MFC](../../mfc/reference/adding-an-mfc-odbc-consumer.md).

Abrir un objeto de tipo dinámico o una instantánea cuando necesite seleccionar registros de un origen de datos. El tipo de objeto que se va a crear depende de lo que necesita hacer con los datos en la aplicación y en qué el controlador ODBC admite. Para obtener más información, consulte [Dynaset](../../data/odbc/dynaset.md) y [instantánea](../../data/odbc/snapshot.md).

#### <a name="to-open-a-recordset"></a>Para abrir un conjunto de registros

1. Construya un objeto de su `CRecordset`-clase derivada.

   Puede construir el objeto en el montón o en el marco de pila de una función.

1. Opcionalmente, modifique el comportamiento del conjunto de registros de forma predeterminada. Para las opciones disponibles, consulte [establecer las opciones de conjunto de registros](#_core_setting_recordset_options).

1. Llamar al objeto [abierto](../../mfc/reference/crecordset-class.md#open) función miembro.

En el constructor, pase un puntero a un `CDatabase` de objeto o pasar NULL para usar un objeto de base de datos temporal que crea el marco de trabajo y se abre en función de la cadena de conexión devuelta por la [GetDefaultConnect](../../mfc/reference/crecordset-class.md#getdefaultconnect) función miembro. La `CDatabase` objeto ya es posible que esté conectado a un origen de datos.

La llamada a `Open` SQL se utiliza para seleccionar registros del origen de datos. El primer registro seleccionado (si existe) es el registro actual. Los valores de campos del registro se almacenan en los miembros de datos de campo del objeto de conjunto de registros. Si se seleccionaron todos los registros, tanto el `IsBOF` y `IsEOF` funciones miembro devuelven 0.

En su [abierto](../../mfc/reference/crecordset-class.md#open) llamada, puede:

- Especifique si el conjunto de registros es un tipo dinámico o una instantánea. Abrir conjuntos de registros como instantáneas de forma predeterminada. O bien, puede especificar un conjunto de registros solo hacia delante que permite desplazamiento sólo hacia delante, un registro a la vez.

   De forma predeterminada, un conjunto de registros usa el tipo predeterminado almacenado en el `CRecordset` miembro de datos `m_nDefaultType`. Asistentes para escribir código para inicializar `m_nDefaultType` para el tipo de conjunto de registros que elija en el asistente. En lugar de aceptar este valor predeterminado, puede sustituir por otro tipo de conjunto de registros.

- Especifique una cadena para reemplazar el valor predeterminado SQL **seleccione** instrucción que crea el conjunto de registros.

- Especifique si el conjunto de registros es de solo lectura o solo para anexar. Conjuntos de registros permiten la actualización de forma predeterminada, completas, pero puede limitar al agregar nuevos registros solo o puede impedir todas las actualizaciones.

El ejemplo siguiente muestra cómo abrir un objeto de instantánea de solo lectura de la clase `CStudentSet`, una clase específica de la aplicación:

```cpp
// Construct the snapshot object
CStudentSet rsStudent( NULL );
// Set options if desired, then open the recordset
if(!rsStudent.Open(CRecordset::snapshot, NULL, CRecordset::readOnly))
    return FALSE;
// Use the snapshot to operate on its records...
```

Después de llamar a `Open`, usar los miembros de datos y funciones de miembro del objeto para trabajar con los registros. En algunos casos, es posible que desee volver a consultar o actualizar el conjunto de registros para incluir los cambios que se han producido en el origen de datos. Para obtener más información, consulte [conjunto de registros: volver a consultar un conjunto de registros (ODBC)](../../data/odbc/recordset-requerying-a-recordset-odbc.md).

> [!TIP]
>  La cadena de conexión que usa durante el desarrollo podría no ser la misma cadena de conexión que necesitan los usuarios eventual. Para obtener ideas sobre cómo generalizar la aplicación en este sentido, consulte [origen de datos: administrar conexiones (ODBC)](../../data/odbc/data-source-managing-connections-odbc.md).

##  <a name="_core_setting_recordset_options"></a> Establecer las opciones de conjunto de registros

Después de crear el objeto de conjunto de registros pero antes de llamar a `Open` para seleccionar registros, es posible que desee establecer algunas opciones para controlar el comportamiento del conjunto de registros. Para todos los conjuntos de registros, hacer lo siguiente:

- Especifique un [filtro](../../data/odbc/recordset-filtering-records-odbc.md) para restringir la selección de registro.

- Especifique un [ordenación](../../data/odbc/recordset-sorting-records-odbc.md) orden para los registros.

- Especificar [parámetros](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md) para que pueda seleccionar registros usando información obtenida o calculada en tiempo de ejecución.

También puede establecer la siguiente opción si las condiciones son adecuadas:

- Si el conjunto de registros es actualizable y admite las opciones de bloqueos, especifique el [bloqueo](../../data/odbc/recordset-locking-records-odbc.md) método usado para las actualizaciones.

> [!NOTE]
>  Para afectar la selección de registros, debe establecer estas opciones antes de llamar a la `Open` función miembro.

##  <a name="_core_closing_a_recordset"></a> Cerrar un conjunto de registros

Cuando termine con el conjunto de registros, debe deshacerse de ellos y desasignar su memoria.

#### <a name="to-close-a-recordset"></a>Para cerrar un conjunto de registros

1. Llame a su [cerrar](../../mfc/reference/crecordset-class.md#close) función miembro.

1. Destruya el objeto de conjunto de registros.

   Si se ha declarado en el marco de pila de una función, el objeto se destruye automáticamente cuando el objeto queda fuera del ámbito. En caso contrario, use el **eliminar** operador.

`Close` Libera el conjunto de registros `HSTMT` controlar. No se destruye el objeto de C++.

## <a name="see-also"></a>Vea también

[Conjunto de registros (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Conjunto de registros: Desplazamiento (ODBC)](../../data/odbc/recordset-scrolling-odbc.md)<br/>
[Conjunto de registros: Agregar, actualizar y eliminar registros (ODBC)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)