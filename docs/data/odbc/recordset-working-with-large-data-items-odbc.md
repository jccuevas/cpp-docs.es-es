---
title: "Conjunto de registros: Trabajar con grandes elementos de datos (ODBC) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "objetos binarios grandes"
  - "BLOB (objeto binario grande), conjuntos de registros"
  - "CLongBinary (clase), utilizar en conjuntos de registros"
  - "conjuntos de registros ODBC, objetos binarios grandes"
  - "conjuntos de registros, objetos binarios grandes"
ms.assetid: 3e80b5a8-b6e7-43c6-a816-e54befc513a3
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# Conjunto de registros: Trabajar con grandes elementos de datos (ODBC)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Este tema se aplica tanto a las clases ODBC como a las clases DAO de MFC.  
  
> [!NOTE]
>  Si utiliza las clases DAO de MFC, administre los grandes elementos de datos mediante la clase [CByteArray](../../mfc/reference/cbytearray-class.md) en lugar de la clase [CLongBinary](../../mfc/reference/clongbinary-class.md).  Si utiliza las clases ODBC de MFC con la obtención de filas masiva, utilice `CLongBinary` en lugar de `CByteArray`.  Para obtener más información sobre la obtención masiva de filas, vea [Conjunto de registros: Obtener registros de forma masiva \(ODBC\)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
 Supongamos que su base de datos puede almacenar grandes fragmentos de datos, como mapas de bits \(fotografías de empleados, mapas, imágenes de productos, objetos OLE, entre otros\).  Este tipo de datos suele denominarse Objeto binario grande u objeto BLOB \(*Binary Large Object\) debido a que:*  
  
-   Todos los valores de campo son grandes.  
  
-   A diferencia de los números y otros tipos de datos sencillos, no tiene un tamaño predecible.  
  
-   Los datos no tienen forma desde la perspectiva del programa.  
  
 Este tema explica la compatibilidad que proporcionan las clases de base de datos para el trabajo con estos objetos.  
  
##  <a name="_core_managing_large_objects"></a> Administrar objetos grandes  
 Los conjuntos de registros tienen dos formas de resolver la especial dificultad de administrar objetos binarios grandes.  Se puede usar la clase [CByteArray](../../mfc/reference/cbytearray-class.md) o la clase [CLongBinary](../../mfc/reference/clongbinary-class.md).  En general, `CByteArray` es la forma preferida de administrar datos binarios de gran tamaño.  
  
 `CByteArray` requiere una mayor sobrecarga que `CLongBinary` pero tiene mayor capacidad, como se describe en [CByteArray \(Clase\)](#_core_the_cbytearray_class).  `CLongBinary` se describe brevemente en [CLongBinary \(Clase\)](#_core_the_clongbinary_class).  
  
 Para obtener información detallada sobre el uso de `CByteArray` para trabajar con grandes elementos de datos, vea la [Nota técnica 45](../../mfc/tn045-mfc-database-support-for-long-varchar-varbinary.md).  
  
##  <a name="_core_the_cbytearray_class"></a> CByteArray \(Clase\)  
 `CByteArray` es una de las clases de colección de la biblioteca MFC.  Los objetos `CByteArray` almacenan una matriz dinámica de bytes, que puede crecer según sea necesario.  La clase proporciona acceso rápido por índice, como en las matrices de C\+\+ integradas.  Se pueden serializar y volcar objetos `CByteArray` con fines de diagnóstico.  La clase proporciona funciones miembro para obtener y establecer bytes específicos, insertar y anexar bytes, y quitar un byte o todos los bytes.  Estas funciones simplifican el análisis de los datos binarios.  Por ejemplo, si el objeto binario es un objeto OLE, puede requerirse procesar algunos bytes de encabezado para alcanzar el objeto propiamente dicho.  
  
##  <a name="_core_using_cbytearray_in_recordsets"></a> Utilizar CByteArray en conjuntos de registros  
 Al dar el tipo `CByteArray` a un miembro de datos de campo del conjunto de registros, se proporciona una base fija a partir de la cual [RFX](../../data/odbc/record-field-exchange-rfx.md) puede administrar la transferencia de ese tipo de objetos entre el conjunto de registros y el origen de datos, y a través de ésta pueden manipularse los datos que contiene el objeto.  RFX necesita una ubicación específica para los datos recuperados, así como una forma de obtener acceso a los datos subyacentes.  
  
 Para obtener información detallada sobre el uso de `CByteArray` para trabajar con grandes elementos de datos, vea la [Nota técnica 45](../../mfc/tn045-mfc-database-support-for-long-varchar-varbinary.md).  
  
##  <a name="_core_the_clongbinary_class"></a> CLongBinary \(Clase\)  
 Un objeto [CLongBinary](../../mfc/reference/clongbinary-class.md) es un *shell* sencillo creado a partir de un identificador `HGLOBAL` que apunta a un bloque de almacenamiento asignado en el montón.  Al enlazar una columna de tabla que contiene un objeto binario grande, RFX asigna el identificador `HGLOBAL` cuando necesita transferir los datos al conjunto de registros y almacena el identificador en el campo `CLongBinary` del conjunto de registros.  
  
 A su vez, se utiliza el identificador `HGLOBAL`, `m_hData`, para trabajar con los datos, usándolo como se haría con los datos de cualquier identificador.  Aquí es donde [CByteArray](../../mfc/reference/cbytearray-class.md) tiene funcionalidad adicional.  
  
> [!CAUTION]
>  Los objetos CLongBinary no pueden usarse como parámetros en llamadas de función.  Asimismo, su implementación, que llama a **::SQLGetData**, necesariamente ralentiza el rendimiento de desplazamiento para una instantánea desplazable.  Esto también puede ocurrir al usar una llamada a **::SQLGetData** para recuperar columnas de esquema dinámicas.  
  
## Vea también  
 [Conjunto de registros \(ODBC\)](../../data/odbc/recordset-odbc.md)   
 [Conjunto de registros: Obtener cálculos SUM y otros resultados agregados \(ODBC\)](../../data/odbc/recordset-obtaining-sums-and-other-aggregate-results-odbc.md)   
 [Intercambio de campos de registros \(RFX\)](../../data/odbc/record-field-exchange-rfx.md)