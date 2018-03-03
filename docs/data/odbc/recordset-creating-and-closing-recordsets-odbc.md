---
title: 'Conjunto de registros: Crear y cerrar conjuntos de registros (ODBC) | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- ODBC recordsets, creating
- recordsets, creating
- recordsets, opening
- recordsets, closing
- ODBC recordsets, closing
- ODBC recordsets, opening
ms.assetid: 8d2aac23-4396-4ce2-8c60-5ecf1b360d3d
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 9ec09c08aa4730c11960d675aef68c8a1007c900
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="recordset-creating-and-closing-recordsets-odbc"></a>Conjunto de registros: Crear y cerrar conjuntos de registros (ODBC)
Este tema es aplicable a las clases ODBC de MFC.  
  
 Para usar un conjunto de registros, construya un objeto de conjunto de registros y, a continuación, llame a su **abiertos** función de miembro para ejecutar la consulta del conjunto de registros y seleccionar los registros. Cuando termine con el conjunto de registros, cierre y destruya el objeto.  
  
 En este tema se explica:  
  
-   [Cuándo y cómo crear un objeto de conjunto de registros](#_core_creating_recordsets_at_run_time).  
  
-   [Cuándo y cómo puede calificar un comportamiento del conjunto de registros de parametrizar, filtrado, ordenación o bloquearla](#_core_setting_recordset_options).  
  
-   [Cuándo y cómo cerrar un objeto de conjunto de registros](#_core_closing_a_recordset).  
  
##  <a name="_core_creating_recordsets_at_run_time"></a>Crear conjuntos de registros en tiempo de ejecución  
 Para poder crear objetos de conjunto de registros en el programa, normalmente se escriben las clases de conjunto de registros específicos de la aplicación. Para obtener más información acerca de este paso preliminar, consulte [agregar un consumidor ODBC de MFC](../../mfc/reference/adding-an-mfc-odbc-consumer.md).  
  
 Abrir un objeto de conjunto de registros dinámicos o una instantánea cuando necesite seleccionar registros de un origen de datos. El tipo de objeto que se va a crear depende de lo que necesita hacer con los datos en la aplicación y en qué el controlador ODBC admite. Para obtener más información, consulte [Dynaset](../../data/odbc/dynaset.md) y [instantánea](../../data/odbc/snapshot.md).  
  
#### <a name="to-open-a-recordset"></a>Para abrir un conjunto de registros  
  
1.  Construir un objeto de su `CRecordset`-clase derivada.  
  
     Puede construir el objeto en el montón o en el marco de pila de una función.  
  
2.  Opcionalmente, modifique el comportamiento predeterminado de conjunto de registros. Las opciones disponibles, consulte [establecer las opciones del conjunto de registros](#_core_setting_recordset_options).  
  
3.  Llamar al objeto [abiertos](../../mfc/reference/crecordset-class.md#open) función miembro.  
  
 En el constructor, pase un puntero a un `CDatabase` objeto o pasar **NULL** para utilizar un archivo temporal objeto de base de datos que el marco de trabajo crea y abre basándose en la cadena de conexión devuelta por la [GetDefaultConnect ](../../mfc/reference/crecordset-class.md#getdefaultconnect) función miembro. La `CDatabase` objeto posible que ya esté conectado a un origen de datos.  
  
 La llamada a **abiertos** utiliza SQL para seleccionar registros del origen de datos. El primer registro seleccionado (si existe) es el registro actual. Los valores de campos del registro se almacenan en los miembros de datos de campo del objeto de conjunto de registros. Si se han seleccionado todos los registros, tanto el `IsBOF` y `IsEOF` funciones miembro devuelven 0.  
  
 En su [abiertos](../../mfc/reference/crecordset-class.md#open) llamada, puede:  
  
-   Especifique si el conjunto de registros es un conjunto de registros dinámicos o una instantánea. Abrir conjuntos de registros como instantáneas de forma predeterminada. O bien, puede especificar un conjunto de registros solo hacia delante que permite desplazamiento solo hacia delante, un registro a la vez.  
  
     De forma predeterminada, un conjunto de registros utiliza el tipo predeterminado almacenado en el `CRecordset` miembro de datos **m_nDefaultType**. Asistentes para escribir código para inicializar **m_nDefaultType** para el tipo de conjunto de registros que elija en el asistente. En lugar de aceptar esta configuración predeterminada, puede sustituir otro tipo de conjunto de registros.  
  
-   Especifique una cadena para reemplazar el código SQL predeterminado **seleccione** instrucción que crea el conjunto de registros.  
  
-   Especifique si el conjunto de registros es de solo lectura o solo de adición. Conjuntos de registros permiten la actualización de forma predeterminada, completas, pero se puede limitar a agregar únicamente nuevos registros o puede prohibir todas las actualizaciones.  
  
 En el ejemplo siguiente se muestra cómo abrir un objeto de instantánea de solo lectura de la clase `CStudentSet`, una clase específica de la aplicación:  
  
```  
// Construct the snapshot object  
CStudentSet rsStudent( NULL );  
// Set options if desired, then open the recordset  
if(!rsStudent.Open(CRecordset::snapshot, NULL, CRecordset::readOnly))  
    return FALSE;  
// Use the snapshot to operate on its records...  
```  
  
 Después de llamar a **abiertos**, usar los miembros de datos y funciones de miembro del objeto para trabajar con los registros. En algunos casos, puede volver a consultar o actualizar el conjunto de registros para incluir cambios que se han producido en el origen de datos. Para obtener más información, consulte [conjunto de registros: volver a consultar un conjunto de registros (ODBC)](../../data/odbc/recordset-requerying-a-recordset-odbc.md).  
  
> [!TIP]
>  La cadena de conexión que se utiliza durante el desarrollo puede no ser la misma cadena de conexión que necesiten los usuarios eventuales. Para obtener ideas sobre cómo generalizar la aplicación en este sentido, vea [origen de datos: administrar conexiones (ODBC)](../../data/odbc/data-source-managing-connections-odbc.md).  
  
##  <a name="_core_setting_recordset_options"></a>Establecer las opciones del conjunto de registros  
 Después de crear el objeto de conjunto de registros, pero antes de llamar a **abiertos** para seleccionar registros, puede establecer algunas opciones para controlar el comportamiento del conjunto de registros. Para todos los conjuntos de registros, hacer lo siguiente:  
  
-   Especifique un [filtro](../../data/odbc/recordset-filtering-records-odbc.md) para restringir la selección de registros.  
  
-   Especifique un [ordenación](../../data/odbc/recordset-sorting-records-odbc.md) orden para los registros.  
  
-   Especifique [parámetros](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md) para que pueda seleccionar registros usando información obtenida o calculada en tiempo de ejecución.  
  
 También puede establecer la siguiente opción si las condiciones son correctas:  
  
-   Si el conjunto de registros es actualizable y admite las opciones de bloqueos, especifique el [bloqueo](../../data/odbc/recordset-locking-records-odbc.md) método usado para las actualizaciones.  
  
> [!NOTE]
>  Para modificar la selección de registros, debe establecer estas opciones antes de llamar a la **abiertos** función miembro.  
  
##  <a name="_core_closing_a_recordset"></a>Cerrar un conjunto de registros  
 Cuando termine con el conjunto de registros, debe deshacerse de ellos y desasignar la memoria asociada.  
  
#### <a name="to-close-a-recordset"></a>Para cerrar un conjunto de registros  
  
1.  Llame a su [cerrar](../../mfc/reference/crecordset-class.md#close) función miembro.  
  
2.  Destruye el objeto de conjunto de registros.  
  
     Si se ha declarado en el marco de pila de una función, el objeto se destruye automáticamente cuando el objeto queda fuera del ámbito. De lo contrario, utilice la **eliminar** operador.  
  
 **Cerrar** libera el conjunto de registros **HSTMT** controlar. No se destruye el objeto de C++.  
  
## <a name="see-also"></a>Vea también  
 [Conjunto de registros (ODBC)](../../data/odbc/recordset-odbc.md)   
 [Conjunto de registros: Desplazamiento (ODBC)](../../data/odbc/recordset-scrolling-odbc.md)   
 [Conjunto de registros: Agregar, actualizar y eliminar registros (ODBC)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)