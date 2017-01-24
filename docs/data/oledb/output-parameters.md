---
title: "Par&#225;metros de salida | Microsoft Docs"
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
  - "OLE DB, procedimientos almacenados"
  - "llamadas a procedimientos"
  - "llamadas a procedimientos, procedimientos almacenados"
  - "procedimientos almacenados, llamar"
  - "procedimientos almacenados, parámetros"
ms.assetid: 4f7c2700-1c2d-42f3-8c9f-7e83962b2442
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Par&#225;metros de salida
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Llamar a un procedimiento almacenado es similar a invocar un comando SQL.  La principal diferencia es que los procedimientos almacenados usan parámetros de salida y valores devueltos.  
  
 En el siguiente procedimiento almacenado, el primer signo de interrogación '?' es el valor devuelto \(phone\) y el segundo es el parámetro de entrada \(name\):  
  
```  
DEFINE_COMMAND(CMySProcAccessor, _T("{ ? = SELECT phone FROM shippers WHERE name = ? }")  
```  
  
 Los parámetros de entrada y salida se especifican en el mapa de parámetros:  
  
```  
BEGIN_PARAM_MAP(CMySProcAccessor)  
   SET_PARAM_TYPE(DBPARAMIO_OUTPUT)  
   COLUMN_ENTRY(1, m_Phone)   // Phone is the return value  
   SET_PARAM_TYPE(DBPARAMIO_INPUT)  
   COLUMN_ENTRY(2, m_Name)   // Name is the input parameter  
END_PARAM_MAP()  
```  
  
 La aplicación debe controlar los resultados devueltos por procedimientos almacenados.  Diferentes proveedores OLE DB devuelven parámetros de salida y valores devueltos en diferentes momentos durante el procesamiento de los resultados.  Por ejemplo, el proveedor OLE DB de Microsoft para SQL Server \(SQLOLEDB\) no proporciona parámetros de salida ni códigos devueltos hasta que el consumidor haya recuperado o cancelado los conjuntos de resultados devueltos por el procedimiento almacenado.  Los resultados se devuelven en el último paquete TDS del servidor.  
  
## Recuento de filas  
 Si utiliza las plantillas de consumidor OLE DB para ejecutar un procedimiento almacenado con parámetros de salida, el recuento de filas no se establece hasta cerrar el conjunto de filas.  
  
 Por ejemplo, considere un procedimiento almacenado con un conjunto de filas y un parámetro de salida:  
  
```  
create procedure sp_test  
   @_rowcount integer output  
as  
   select top 50 * from test  
   @_rowcount = @@rowcount  
return 0  
```  
  
 El parámetro de salida @\_rowcount informa del número de filas devueltas realmente por la tabla de prueba.  Sin embargo, este procedimiento almacenado limita el número de filas a un máximo de 50.  Por ejemplo, si hay 100 filas en la prueba, el recuento de filas daría 50 \(porque este código recupera solo las 50 primeras filas\).  Si hubiera solo 30 filas en la tabla, el recuento de filas sería 30.  Deberá llamar a **Close** o **CloseAll** para rellenar el parámetro de salida antes de recuperar ese valor.  
  
## Vea también  
 [Utilizar procedimientos almacenados](../../data/oledb/using-stored-procedures.md)