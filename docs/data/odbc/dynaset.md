---
title: "Conjunto de registros din&#225;micos | Microsoft Docs"
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
  - "biblioteca de cursores [ODBC], disponibilidad de los conjuntos de registros dinámicos"
  - "cursores [ODBC], cursores controlados mediante conjuntos de claves en conjuntos de registros dinámicos"
  - "conjuntos de registros dinámicos"
  - "cursores controlados mediante conjuntos de claves en conjuntos de registros dinámicos"
  - "biblioteca de cursores ODBC [ODBC], conjuntos de registros dinámicos"
  - "conjuntos de registros ODBC, conjuntos de registros dinámicos"
  - "conjuntos de registros [C++], conjuntos de registros dinámicos"
ms.assetid: 2867e6be-208e-4fe7-8bbe-b8697cb1045c
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Conjunto de registros din&#225;micos
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Este tema describe los conjuntos de registros dinámicos y explica su [disponibilidad](#_core_availability_of_dynasets).  
  
> [!NOTE]
>  Este tema es aplicable a las clases ODBC de MFC, incluida [CRecordset](../../mfc/reference/crecordset-class.md).  Para obtener más información sobre los conjuntos de registros dinámicos de las clases DAO, vea [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md).  Con DAO, se pueden abrir conjuntos de registros de tipo dinámico.  
  
 Un conjunto de registros dinámico es un conjunto de registros con propiedades dinámicas.  Durante su existencia, un objeto de conjunto de registros en modo dinámico \(denominado normalmente conjunto de registros dinámico\) permanece sincronizado con el origen de datos de la siguiente forma.  En un entorno multiusuario, otros usuarios podrían editar o eliminar los registros que están en el conjunto de registros dinámico o agregar registros a la tabla que representa.  Los registros que la aplicación agrega o elimina en el conjunto de registros quedan reflejados en el conjunto de registros dinámico.  Los registros que otros usuarios agregan a la tabla no se reflejarán en el conjunto de registros dinámico hasta que se recompile este llamando a la función miembro **Requery**.  Cuando otros usuarios eliminan registros, el código MFC pasa por alto las eliminaciones del conjunto de registros.  Los cambios de edición efectuados por otros usuarios en registros existentes quedan reflejados en el conjunto de registros dinámico al desplazarse al registro en cuestión.  
  
 De forma similar, los cambios de edición personales en registros de un conjunto de registros dinámico quedan reflejados en los conjuntos de registros dinámicos que están utilizando otros usuarios.  Los registros que se agregan no quedan reflejados en los conjuntos de registros dinámicos de otros usuarios hasta que realicen una nueva consulta a los mismos.  Los registros que se eliminan se marcan como "eliminados" en los conjuntos de registros de otros usuarios.  Si se tienen varias conexiones a la misma base de datos \(varios objetos `CDatabase`\), los conjuntos de registros asociados a dichas conexiones tienen el mismo estado que los conjuntos de registros de otros usuarios.  
  
 Los conjuntos de registros dinámicos son muy útiles cuando los datos deben ser dinámicos; por ejemplo, en un sistema de reserva de vuelos.  
  
> [!NOTE]
>  Para usar conjuntos de registros dinámicos, se debe tener un controlador ODBC para el origen de datos que los admita y no debe estar cargada la biblioteca de cursores ODBC.  Para obtener más información, vea [Disponibilidad de los conjuntos de registros dinámicos](#_core_availability_of_dynasets).  
  
 Para especificar que un conjunto de registros sea dinámico, hay que pasar **CRecordset::dynaset** como primer parámetro a la función miembro **Open** del objeto de conjunto de registros.  
  
> [!NOTE]
>  En el caso de conjuntos de registros dinámicos actualizables, el controlador ODBC debe admitir instrucciones de actualización con ubicación o la función de la API de ODBC **::SQLSetPos**.  Si se admiten ambas, MFC utiliza **::SQLSetPos** porque es más eficaz.  
  
##  <a name="_core_availability_of_dynasets"></a> Disponibilidad de los conjuntos de registros dinámicos  
 Las clases de base de datos MFC admiten conjuntos de registros dinámicos si se satisfacen los siguientes requisitos:  
  
-   La biblioteca de cursores ODBC DLL no se debe estar utilizando para este origen de datos.  
  
     Si se utiliza la biblioteca de cursores, enmascara parte de la funcionalidad del controlador ODCB subyacente que es necesario para la compatibilidad con los conjuntos de registros dinámicos.  Si desea utilizar conjuntos de registros dinámicos \(y el controlador ODBC posee la funcionalidad requerida para estos conjuntos, como se describe en el resto de esta sección\), se puede hacer que MFC no cargue la biblioteca de cursores al crear un objeto `CDatabase`.  Para obtener más información, vea [ODBC](../../data/odbc/odbc-basics.md) y la función miembro [OpenEx](../Topic/CDatabase::OpenEx.md) u [Open](../Topic/CDatabase::Open.md) de la clase `CDatabase`.  
  
     En terminología ODBC, los conjuntos de registros dinámicos y las instantáneas se denominan cursores.  Un cursor es un mecanismo utilizado para mantener el seguimiento de su posición en un conjunto de registros.  
  
-   El controlador ODBC para el origen de datos debe ser compatible con cursores dirigidos por conjuntos de claves.  
  
     Los cursores dirigidos por conjuntos de claves administran los datos de una tabla mediante la obtención y almacenamiento de un conjunto de claves.  Las claves se usan para obtener datos actuales de la tabla cuando el usuario se desplaza a un registro concreto.  Para determinar si el controlador proporciona esta compatibilidad, llame a la función de la API de ODBC **::SQLGetInfo** con el parámetro **SQL\_SCROLL\_OPTIONS**.  
  
     Si se intenta abrir un conjunto de registros dinámico que no es compatible con el conjunto de claves, se obtiene una excepción `CDBException` con el valor de código devuelto **AFX\_SQL\_ERROR\_DYNASET\_NOT\_SUPPORTED**.  
  
-   El controlador ODBC para el origen de datos debe admitir obtención extendida.  
  
     La obtención extendida es la posibilidad de desplazarse hacia atrás y hacia delante por los registros resultantes de la consulta SQL.  Para determinar si el controlador admite esta capacidad, llame a la función de la API de ODBC **::SQLGetFunctions** con el parámetro **SQL\_API\_SQLEXTENDEDFETCH**.  
  
 Si se desean conjuntos de registros dinámicos actualizables \(o instantáneas\), el controlador ODBC también debe admitir la función de la API de ODBC **::SQLSetPos** o actualizaciones con ubicación.  La función **::SQLSetPos** permite a MFC actualizar el origen de datos sin enviar instrucciones SQL.  Si esta compatibilidad está disponible, MFC prefiere utilizarla antes que hacer actualizaciones mediante SQL.  Para determinar si el controlador admite **::SQLSetPos**, hay que llamar a **::SQLGetInfo** con el parámetro **SQL\_POS\_OPERATIONS**.  
  
 Sintaxis SQL de uso de actualizaciones con ubicación \(de cursorname de **WHERE CURRENT OF** \<del formulario\>\) para identificar una fila determinada en la tabla del origen de datos.  Para determinar si el controlador admite actualizaciones con ubicación, hay que llamar a **::SQLGetInfo** con el parámetro **SQL\_POSITIONED\_STATEMENTS**.  
  
 Generalmente, los conjuntos de registros dinámicos de MFC \(pero no los conjuntos de registros sólo hacia delante\) necesitan un controlador ODBC que sea compatible con la API de nivel 2.  Si el controlador del origen de datos es compatible con la API de nivel 1, se pueden seguir utilizando tanto instantáneas actualizables y de sólo lectura como conjuntos de registros sólo hacia delante, pero no conjuntos de registros dinámicos.  No obstante, un controlador de nivel 1 puede admitir conjuntos de registros dinámicos si admite obtención extendida y cursores dirigidos por conjuntos de claves.  Para obtener más información sobre los niveles de compatibilidad ODBC, vea [ODBC](../../data/odbc/odbc-basics.md).  
  
> [!NOTE]
>  Si se desea utilizar tanto instantáneas como conjuntos de registros dinámicos, se debe basar en dos objetos `CDatabase` distintos \(dos conexiones distintas\).  
  
 A diferencia de las instantáneas, que usan almacenamiento intermedio mantenido por la biblioteca de cursores ODBC, los conjuntos de registros dinámicos obtienen un registro directamente del origen de datos tan pronto como se realice el desplazamiento a dicho registro.  Esto hace que los registros seleccionados originalmente por el conjunto de registros dinámicos permanezcan sincronizados con el origen de datos.  
  
 Vea [Lista de controladores ODBC](../../data/odbc/odbc-driver-list.md) para obtener una lista de los controladores ODBC incluidos en esta versión de Visual C\+\+ e información sobre cómo obtener controladores adicionales.  
  
## Vea también  
 [Conectividad abierta de bases de datos \(ODBC\)](../../data/odbc/open-database-connectivity-odbc.md)