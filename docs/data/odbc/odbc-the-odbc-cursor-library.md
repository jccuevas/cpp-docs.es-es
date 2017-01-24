---
title: "ODBC: Biblioteca de cursores ODBC | Microsoft Docs"
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
  - "biblioteca de cursores [ODBC]"
  - "biblioteca de cursores [ODBC], instantáneas"
  - "cursores, biblioteca de cursores ODBC"
  - "controladores ODBC de nivel 1"
  - "biblioteca de cursores ODBC [ODBC]"
  - "controladores ODBC, compatibilidad con cursores"
  - "controladores ODBC, nivel 1"
  - "ODBC, marca de tiempo"
  - "actualizaciones con ubicación"
  - "colocar cursores"
  - "instantáneas, compatibilidad de ODBC"
  - "cursores estáticos"
  - "marcas de tiempo, columnas de marca de tiempo ODBC"
ms.assetid: 6608db92-82b1-4164-bb08-78153c227be3
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ODBC: Biblioteca de cursores ODBC
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Este tema describe la biblioteca de cursores ODBC y explica su uso.  Para obtener más información, vea:  
  
-   [Biblioteca de cursores y controladores ODBC de nivel 1](#_core_the_cursor_library_and_level_1_odbc_drivers)  
  
-   [Actualizaciones con ubicación y columnas de marca de tiempo](#_core_positioned_updates_and_timestamp_columns)  
  
-   [Utilizar la biblioteca de cursores](#_core_using_the_cursor_library)  
  
 La biblioteca de cursores ODBC es una biblioteca de vínculos dinámicos \(DLL\) que se encuentra entre el Administrador de controladores ODBC y el controlador.  En términos de ODBC, un controlador conserva un cursor para realizar un seguimiento de su posición en el conjunto de registros.  El cursor marca la posición en el conjunto de registros al que ya se ha desplazado el usuario, el registro actual.  
  
##  <a name="_core_the_cursor_library_and_level_1_odbc_drivers"></a> Biblioteca de cursores y controladores ODBC de nivel 1  
 La biblioteca de cursores ODBC proporciona a los controladores de nivel 1 las siguientes capacidades nuevas:  
  
-   Desplazamiento hacia delante y hacia atrás.  Los controladores de nivel 2 no necesitan la biblioteca de cursores porque ya se pueden desplazar.  
  
-   Compatibilidad con instantáneas.  La biblioteca de cursores administra un búfer que contiene los registros de las instantáneas.  Este búfer refleja las eliminaciones y las ediciones en registros de su programa, pero no las adiciones, eliminaciones ni ediciones de otros usuarios.  Por consiguiente, la instantánea está tan actualizada como lo esté el búfer de la biblioteca de cursores.  El búfer tampoco refleja las adiciones personales hasta que se llama a **Requery**.  Los conjuntos de registros dinámicos no utilizan la biblioteca de cursores.  
  
 La biblioteca de cursores asigna instantáneas \(cursores estáticos\) aunque no sean normalmente compatibles con el controlador.  Si el controlador es compatible con los cursores estáticos, no es necesario cargar la biblioteca de cursores para obtener compatibilidad con la instantánea.  Si se utiliza la biblioteca de cursores, sólo se pueden utilizar instantáneas y conjuntos de registros sólo hacia delante.  Si el controlador es compatible con conjuntos de registros dinámicos \(cursores KEYSET\_DRIVEN\) y se desea utilizarlos, no debe utilizarse la biblioteca de cursores.  Si se desea utilizar instantáneas y conjuntos de registros dinámicos, se deben basar en dos objetos `CDatabase` distintos \(dos conexiones distintas\) a menos que el controlador sea compatible con ambos.  
  
##  <a name="_core_positioned_updates_and_timestamp_columns"></a> Actualizaciones con ubicación y columnas de marca de tiempo  
  
> [!NOTE]
>  Mediante las clases ODBC de MFC, como se describe en este tema, o las clases DAO de MFC se puede tener acceso a los orígenes de datos ODBC.  
  
> [!NOTE]
>  Si el controlador ODBC admite **SQLSetPos**, que MFC utiliza si está disponible, este tema no afecta al usuario.  
  
 La mayoría de los controladores de nivel 1 no admiten actualizaciones con ubicación.  Estos controladores se basan en la biblioteca de cursores para emular las capacidades de los controladores de nivel 2 en este aspecto.  La biblioteca de cursores emula la compatibilidad con actualizaciones con ubicación por medio de una actualización con búsqueda en los campos inalterados.  
  
 En algunos casos, un conjunto de registros puede contener una columna de marca de tiempo como uno de dichos campos inalterados.  Cuando se utilizan conjuntos de registros de MFC con tablas que contienen columnas de marca de tiempo surgen dos cuestiones.  
  
 La primera cuestión se refiere a las instantáneas actualizables en tablas con columnas de marca de tiempo.  Si la tabla a la que está enlazado la instantánea contiene una columna de marca de tiempo, se debe llamar a **Requery** después de llamar a **Edit** y **Update**.  En caso contrario, tal vez no se pueda editar de nuevo el mismo registro.  Cuando se llama a **Edit** y después a **Update**, el registro se escribe en el origen de datos y la columna de marca de tiempo se actualiza.  Si no se llama a **Requery**, el valor de marca de tiempo del registro de la instantánea dejará de coincidir con la marca de tiempo correspondiente en el origen de datos.  Si se intenta actualizar de nuevo el registro, puede que el origen de datos no permita la actualización por falta de coincidencia.  
  
 La segunda cuestión se refiere a las limitaciones de la clase [CTime](../../atl-mfc-shared/reference/ctime-class.md) cuando se utiliza con la función `RFX_Date` para transferir información sobre fecha y hora a una tabla o desde la misma.  El procesamiento del objeto `CTime` supone una sobrecarga en forma de procesamiento adicional intermedio durante la transferencia de datos.  El intervalo de fechas de los objetos `CTime` también puede suponer una limitación para algunas aplicaciones.  Una nueva versión de la función `RFX_Date` toma un parámetro ODBC **TIMESTAMP\_STRUCT** en lugar de un objeto `CTime`.  Para obtener más información, vea `RFX_Date` en [Macros y funciones globales](../Topic/Macros,%20Global%20Functions,%20and%20Global%20Variables.md) en la *Referencia de MFC*.  
  
##  <a name="_core_using_the_cursor_library"></a> Utilizar la biblioteca de cursores  
 Cuando se conecta a un origen de datos, llamando a [CDatabase::OpenEx](../Topic/CDatabase::OpenEx.md) o a [CDatabase::Open](../Topic/CDatabase::Open.md), puede especificar si se utiliza la biblioteca de cursores para el origen de datos.  Si va a crear instantáneas en dicho origen de datos, especifique la opción **CDatabase::useCursorLib** para el parámetro `dwOptions` en `OpenEx`, o especifique **TRUE** para el parámetro **bUseCursorLib** en **Open** \(el valor predeterminado es **TRUE**\).  Si el controlador ODBC es compatible con conjuntos de registros dinámicos y desea abrir este tipo de conjuntos en el origen de datos, no utilice la biblioteca de cursores, dado que enmascara parte de la funcionalidad del controlador necesaria para los conjuntos de registros dinámicos.  En ese caso, no especifique **CDatabase::useCursorLib** en `OpenEx` ni especifique **FALSE** para el parámetro **bUseCursorLib** en **Open**.  
  
## Vea también  
 [Conceptos básicos de ODBC](../../data/odbc/odbc-basics.md)