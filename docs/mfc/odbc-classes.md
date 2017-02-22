---
title: "Clases de ODBC | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.classes.data"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "clases de base de datos [C++], ODBC"
  - "clases ODBC [C++]"
ms.assetid: 6c40fca8-3033-4873-9abe-7f51725de0e0
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# Clases de ODBC
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Estas clases funcionan con otras clases de aplicación para dar acceso fácil a una gran variedad de bases de datos para los controladores ODBC \(Open Database Connectivity\) están disponibles.  
  
 Los programas que utilizan las bases de datos ODBC tienen al menos un objeto de `CDatabase` y un objeto de `CRecordset` .  
  
 [CDatabase](../mfc/reference/cdatabase-class.md)  
 Encapsula una conexión a un origen de datos, con el que puede trabajar con el origen de datos.  
  
 [CRecordset](../mfc/reference/crecordset-class.md)  
 Encapsula un conjunto de registros seleccionados de un origen de datos.  Desplazamiento habilitado conjuntos de registros del registro, actualizar los registros \(agregar, editar, y eliminar registros\), calificando la selección con un filtro, ordenar la selección, y parametrizar la selección con información obtenida o calculada en tiempo de ejecución.  
  
 [CRecordView](../mfc/reference/crecordview-class.md)  
 Proporciona una vista de formulario directamente conectada a un objeto de conjunto de registros.  Intercambia datos de intercambio de datos del mecanismo de diálogo \(DDX\) entre el conjunto de registros y los controles de la vista de registros.  Como todas las vistas de formulario, una vista de registros se basa en un recurso de plantilla de cuadro de diálogo.  Registro de las vistas el desplazamiento también admiten entre los registros del conjunto de registros, actualizar registros y, al cerrar el conjunto de registros asociado cuando se cierra la vista de registros.  
  
 [CDBException](../mfc/reference/cdbexception-class.md)  
 Una excepción resultando de errores en el procesamiento de acceso a datos.  Esta clase responde al mismo propósito que otras clases de excepción en el mecanismo excepción\- que administra desde la biblioteca de clases.  
  
 [CFieldExchange](../mfc/reference/cfieldexchange-class.md)  
 Información de contexto de fuentes para admitir el intercambio de campos de registros \(RFX\), que MFC intercambia datos entre los miembros de datos de campo y los miembros de datos de parámetro de un objeto de conjunto de registros y las columnas de la tabla correspondientes en el origen de datos.  Análogo a la clase [CDataExchange](../mfc/reference/cdataexchange-class.md), que se utiliza de manera similar para el diálogo intercambio de datos \(DDX\).  
  
## Clases relacionadas  
 [CLongBinary](../mfc/reference/clongbinary-class.md)  
 Encapsula un identificador al almacenamiento para un objeto binario grande \(BLOB\), como un mapa de bits.  los objetos de`CLongBinary` se utilizan para administrar los objetos de datos grandes almacenados en tablas de base de datos.  
  
 [CDBVariant](../mfc/reference/cdbvariant-class.md)  
 Permite almacenar un valor sin preocuparse de tipo de datos del valor.  `CDBVariant` sigue el tipo de datos del valor actual, que se almacena en una combinación.  
  
## Vea también  
 [Información general de clases](../mfc/class-library-overview.md)