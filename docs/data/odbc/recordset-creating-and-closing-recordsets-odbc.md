---
title: 'Conjunto de registros: Crear y cerrar conjuntos de registros (ODBC)'
ms.date: 05/09/2019
helpviewer_keywords:
- ODBC recordsets, creating
- recordsets, creating
- recordsets, opening
- recordsets, closing
- ODBC recordsets, closing
- ODBC recordsets, opening
ms.assetid: 8d2aac23-4396-4ce2-8c60-5ecf1b360d3d
ms.openlocfilehash: 155b51debfb6eacd3cbdd3293875274ca2dc4ab5
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80212984"
---
# <a name="recordset-creating-and-closing-recordsets-odbc"></a>Conjunto de registros: Crear y cerrar conjuntos de registros (ODBC)

> [!NOTE]
> El Asistente para consumidores ODBC de MFC no está disponible en Visual Studio 2019 ni en versiones posteriores. Aun así, puede crear un consumidor de forma manual.

Este tema es aplicable a las clases ODBC de MFC.

Para usar un conjunto de registros, construya un objeto de conjunto de registros y, después, llame a su función miembro `Open` para ejecutar la consulta y seleccionar los registros. Cuando termine con el conjunto de registros, cierre y destruya el objeto.

En este tema se explica:

- [Cuándo y cómo se puede crear un objeto de conjunto de registros](#_core_creating_recordsets_at_run_time).

- [Cuándo y cómo se puede calificar el comportamiento del conjunto de registros mediante su parametrización, filtrado, ordenación o bloqueo](#_core_setting_recordset_options).

- [Cuándo y cómo se puede cerrar un objeto de conjunto de registros](#_core_closing_a_recordset).

##  <a name="creating-recordsets-at-run-time"></a><a name="_core_creating_recordsets_at_run_time"></a> Creación de conjuntos de registros en tiempo de ejecución

Para poder crear objetos de conjunto de registro en el programa, normalmente primero se escriben las clases de conjunto de registro específicas de la aplicación. Para obtener más información sobre este paso preliminar, vea [Agregar un consumidor ODBC de MFC](../../mfc/reference/adding-an-mfc-odbc-consumer.md).

Abra un objeto de instantánea o dynaset cuando necesite seleccionar registros de un origen de datos. El tipo de objeto que cree dependerá de lo que necesite hacer con los datos de la aplicación y de lo que admita el controlador ODBC. Para obtener más información, vea [Dynaset](../../data/odbc/dynaset.md) e [Instantánea](../../data/odbc/snapshot.md).

#### <a name="to-open-a-recordset"></a>Para abrir un conjunto de registros

1. Construya un objeto de su clase derivada de `CRecordset`.

   Puede construir el objeto en el montón o en el marco de pila de una función.

1. Opcionalmente, modifique el comportamiento predeterminado del conjunto de registros. Para conocer las opciones disponibles, vea [Establecer las opciones del conjunto de registros](#_core_setting_recordset_options).

1. Llame a la función miembro [Open](../../mfc/reference/crecordset-class.md#open) del objeto.

En el constructor, pase un puntero a un objeto `CDatabase` o pase NULL para usar un objeto de base de datos temporal que el marco crea y abre en función de la cadena de conexión devuelta por la función miembro [GetDefaultConnect](../../mfc/reference/crecordset-class.md#getdefaultconnect). El objeto `CDatabase` ya podría estar conectado a un origen de datos.

La llamada a `Open` usa SQL para seleccionar registros del origen de datos. El primer registro seleccionado (si existe) es el registro actual. Los valores de los campos de este registro se almacenan en los miembros de datos de campo del objeto de conjunto de registros. Si se selecciona algún registro, las funciones miembro `IsBOF` y `IsEOF` devuelven 0.

En la llamada a [Open](../../mfc/reference/crecordset-class.md#open), puede:

- Especificar si el conjunto de registros es un dynaset o una instantánea. Los conjuntos de registros se abren como instantáneas de forma predeterminada. También puede especificar un conjunto de registros de solo avance, que permite el desplazamiento solo hacia delante, un registro de cada vez.

   De forma predeterminada, un conjunto de registros usa `CRecordset`, el tipo predeterminado que está almacenado en el miembro de datos `m_nDefaultType`. Los asistentes escriben código para inicializar `m_nDefaultType` en el tipo de conjunto de registros que elija en el asistente. En lugar de aceptar este valor predeterminado, puede sustituirlo por otro tipo de conjunto de registros.

- Especificar una cadena para reemplazar la instrucción **SELECT** de SQL predeterminada que construye el conjunto de registros.

- Especificar si el conjunto de registros es de solo lectura o de solo anexión. Los conjuntos de registros permiten la actualización completa de forma predeterminada, pero puede limitarlo solo a la adición de nuevos registros o deshabilitar las actualizaciones.

En el ejemplo siguiente se muestra cómo se abre un objeto de instantánea de solo lectura de la clase `CStudentSet`, una clase específica de la aplicación:

```cpp
// Construct the snapshot object
CStudentSet rsStudent( NULL );
// Set options if desired, then open the recordset
if(!rsStudent.Open(CRecordset::snapshot, NULL, CRecordset::readOnly))
    return FALSE;
// Use the snapshot to operate on its records...
```

Después de llamar a `Open`, puede usar las funciones miembro y los miembros de datos del objeto para trabajar con los registros. En algunos casos, es posible que le interese volver a consultar o actualizar el conjunto de registros para incluir los cambios que se han producido en el origen de datos. Para obtener más información, vea [conjunto de registros: reconsultar un conjunto de registros (ODBC)](../../data/odbc/recordset-requerying-a-recordset-odbc.md).

> [!TIP]
>  La cadena de conexión que usa durante el desarrollo podría no ser la misma que necesitan los usuarios finales. Para obtener ideas sobre cómo generalizar la aplicación en este sentido, vea [origen de datos: administrar conexiones (ODBC)](../../data/odbc/data-source-managing-connections-odbc.md).

##  <a name="setting-recordset-options"></a><a name="_core_setting_recordset_options"></a> Establecer las opciones del conjunto de registros

Después de construir el objeto de conjunto de registros, pero antes de llamar a `Open` para seleccionar los registros, es posible que le interese establecer algunas opciones para controlar el comportamiento del conjunto de registros. En todos los conjuntos de registros, puede hacer lo siguiente:

- Especificar un [filtro](../../data/odbc/recordset-filtering-records-odbc.md) para restringir la selección de registros.

- Especificar un criterio de [ordenación](../../data/odbc/recordset-sorting-records-odbc.md) para los registros.

- Especificar [parámetros](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md) para poder seleccionar registros mediante el uso de la información obtenida o calculada en tiempo de ejecución.

También puede establecer la siguiente opción si las condiciones son adecuadas:

- Si el conjunto de registros es actualizable y admite opciones de bloqueo, especifique el método de [bloqueo](../../data/odbc/recordset-locking-records-odbc.md) usado para las actualizaciones.

> [!NOTE]
>  Para influir en la selección de registros, debe establecer estas opciones antes de llamar a la función miembro `Open`.

##  <a name="closing-a-recordset"></a><a name="_core_closing_a_recordset"></a> Cerrar un conjunto de registros

Cuando termine con el conjunto de registros, debe deshacerse de él y desasignar su memoria.

#### <a name="to-close-a-recordset"></a>Para cerrar un conjunto de registros

1. Llame a su función miembro [Close](../../mfc/reference/crecordset-class.md#close).

1. Destruya el objeto de conjunto de registros.

   Si lo ha declarado en el marco de pila de una función, el objeto se destruye automáticamente cuando sale del ámbito. En caso contrario, use el operador **delete**.

`Close` libera el controlador `HSTMT` del conjunto de registros, no destruye el objeto de C++.

## <a name="see-also"></a>Consulte también

[Conjunto de registros (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Conjunto de registros: Desplazamiento (ODBC)](../../data/odbc/recordset-scrolling-odbc.md)<br/>
[Conjunto de registros: Agregar, actualizar y eliminar registros (ODBC)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)
