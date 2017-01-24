---
title: "Conjunto de registros: Crear y cerrar conjuntos de registros (ODBC) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "conjuntos de registros ODBC, cerrar"
  - "conjuntos de registros ODBC, crear"
  - "conjuntos de registros ODBC, abrir"
  - "conjuntos de registros, cerrar"
  - "conjuntos de registros, crear"
  - "conjuntos de registros, abrir"
ms.assetid: 8d2aac23-4396-4ce2-8c60-5ecf1b360d3d
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Conjunto de registros: Crear y cerrar conjuntos de registros (ODBC)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Este tema es aplicable a las clases ODBC de MFC.  
  
 Para usar un conjunto de registros, cree un objeto de conjunto de registros y llame a su función miembro **Open** para ejecutar la consulta correspondiente y seleccionar registros.  Al terminar el trabajo con el conjunto de registros, cierre y destruya el objeto.  
  
 En este tema se explica:  
  
-   [Cuándo y cómo crear un objeto de conjunto de registros](#_core_creating_recordsets_at_run_time).  
  
-   [Cuándo y cómo modificar el comportamiento de un conjunto de registros parametrizándolo, filtrándolo, ordenándolo o bloqueándolo](#_core_setting_recordset_options).  
  
-   [Cuándo y cómo cerrar un objeto de conjunto de registros](#_core_closing_a_recordset).  
  
##  <a name="_core_creating_recordsets_at_run_time"></a> Crear conjuntos de registros en tiempo de ejecución  
 Antes de crear objetos de conjunto de registros en el programa, deberá crear clases de conjunto de registros específicas para la aplicación.  Para obtener más información acerca de este paso previo, vea [Agregar un consumidor ODBC de MFC](../../mfc/reference/adding-an-mfc-odbc-consumer.md).  
  
 Abra un conjunto de registros dinámico o una instantánea cuando necesite seleccionar registros de un origen de datos.  El tipo de objeto creado depende de qué se necesita hacer con los datos en la aplicación y de qué orígenes de datos admite el controlador ODBC.  Para obtener más información, vea [Conjunto de registros dinámicos](../../data/odbc/dynaset.md) e [Instantáneas](../../data/odbc/snapshot.md).  
  
#### Para abrir un conjunto de registros  
  
1.  Cree un objeto de la clase derivada de `CRecordset`.  
  
     Puede crear el objeto en el montón o en el marco de pila de una función.  
  
2.  Opcionalmente, modifique el comportamiento predeterminado del conjunto de registros.  Para ver las opciones disponibles, vea [Establecer las opciones de un conjunto de registros](#_core_setting_recordset_options).  
  
3.  Llame a la función miembro [Open](../Topic/CRecordset::Open.md) del objeto.  
  
 En el constructor, pase un puntero a un objeto `CDatabase` o pase **NULL** para utilizar un objeto temporal de base de datos que el marco de trabajo crea y abre basándose en una cadena de conexión devuelta por la función miembro [GetDefaultConnect](../Topic/CRecordset::GetDefaultConnect.md).  El objeto `CDatabase` puede que ya esté conectado a un origen de datos.  
  
 La llamada a **Open** utiliza SQL para seleccionar registros del origen de datos.  El primer registro seleccionado \(si lo hay\) es el registro actual.  Los valores de los campos de dicho registro se almacenan en los miembros de datos de campo del objeto de conjunto de registros.  Si hay registros seleccionados, las dos funciones miembro `IsBOF` y `IsEOF` devuelven 0.  
  
 En la llamada a [Open](../Topic/CRecordset::Open.md), se puede:  
  
-   Especificar si el conjunto de registros es de tipo dinámico o una instantánea.  Abrir los conjuntos de registros como instantáneas de forma predeterminada.  O bien, especificar un conjunto de registros sólo hacia delante que únicamente permita el desplazamiento hacia delante, de registro en registro.  
  
     De forma predeterminada, los conjuntos de registros usan el tipo predeterminado almacenado en el miembro de datos de `CRecordset` **m\_nDefaultType**.  Los asistentes crean código para inicializar **m\_nDefaultType** con el tipo de conjunto de registros elegido en el asistente.  En lugar de aceptar esta configuración predeterminada, se puede usar otro tipo de conjunto de registros.  
  
-   Especificar una cadena para reemplazar la instrucción SQL **SELECT** predeterminada que crea el conjunto de registros.  
  
-   Especificar si el conjunto de registros es de sólo lectura o de sólo anexar.  Los conjuntos de registros permiten la actualización completa de forma predeterminada, pero se puede limitar a agregar únicamente nuevos registros o se pueden impedir todas las actualizaciones.  
  
 El siguiente ejemplo muestra cómo abrir una instantánea de sólo lectura de la clase `CStudentSet`, una clase específica de la aplicación:  
  
```  
// Construct the snapshot object  
CStudentSet rsStudent( NULL );  
// Set options if desired, then open the recordset  
if(!rsStudent.Open(CRecordset::snapshot, NULL, CRecordset::readOnly))  
    return FALSE;  
// Use the snapshot to operate on its records...  
```  
  
 Después de llamar a **Open**, use las funciones miembro y los miembros de datos del objeto para trabajar con los registros.  En algunos casos, es conveniente realizar una nueva consulta o actualizar el conjunto de registros para incluir cambios que puedan haberse producido en el origen de datos.  Para obtener más información, vea [Conjunto de registros: Volver a consultar un conjunto de registros \(ODBC\)](../../data/odbc/recordset-requerying-a-recordset-odbc.md).  
  
> [!TIP]
>  La cadena de conexión que utilice durante el desarrollo puede no ser la misma que necesiten los usuarios eventuales.  Para obtener ideas sobre cómo generalizar la aplicación en este sentido, vea [Origen de datos: Administrar conexiones \(ODBC\)](../../data/odbc/data-source-managing-connections-odbc.md).  
  
##  <a name="_core_setting_recordset_options"></a> Establecer opciones de conjunto de registros  
 Después de crear un objeto de conjunto de registros y antes de llamar a **Open** para seleccionar registros, es conveniente establecer algunas opciones para controlar el comportamiento del conjunto de registros.  Para todos los conjuntos de registros, se puede:  
  
-   Especificar un [filtro](../../data/odbc/recordset-filtering-records-odbc.md) para restringir la selección de registros.  
  
-   Especificar un criterio de [ordenación](../../data/odbc/recordset-sorting-records-odbc.md) para los registros.  
  
-   Especificar [parámetros](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md) para poder seleccionar registros usando información obtenida o calculada en tiempo de ejecución.  
  
 También se puede establecer la siguiente opción si las condiciones son adecuadas:  
  
-   Si el conjunto de registros es actualizable y admite las opciones de bloqueo, especifique el método de [bloqueo](../../data/odbc/recordset-locking-records-odbc.md) usado para las actualizaciones.  
  
> [!NOTE]
>  Para modificar la selección de registros, se deben establecer estas opciones antes de llamar a la función miembro **Open**.  
  
##  <a name="_core_closing_a_recordset"></a> Cerrar un conjunto de registros  
 Al terminar de trabajar con el conjunto de registros, se debe eliminar y desasignar la memoria asociada.  
  
#### Para cerrar un conjunto de registros  
  
1.  Llame a la función miembro [Close](../Topic/CRecordset::Close.md).  
  
2.  Destruya el objeto de conjunto de registros.  
  
     Si lo declaró en el marco de pila de una función, el objeto se destruye automáticamente cuando el objeto queda fuera del ámbito.  En cualquier otro caso, use el operador **delete**.  
  
 **Close** libera el identificador **HSTMT** del conjunto de registros.  No destruye el objeto de C\+\+.  
  
## Vea también  
 [Conjunto de registros \(ODBC\)](../../data/odbc/recordset-odbc.md)   
 [Conjunto de registros: Desplazamiento \(ODBC\)](../../data/odbc/recordset-scrolling-odbc.md)   
 [Conjunto de registros: Agregar, actualizar y eliminar registros \(ODBC\)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)