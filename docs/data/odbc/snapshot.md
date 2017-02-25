---
title: "Instant&#225;nea | Microsoft Docs"
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
  - "biblioteca de cursores [ODBC], instantáneas"
  - "cursores [ODBC], static"
  - "biblioteca de cursores ODBC [ODBC], instantáneas"
  - "conjuntos de registros ODBC, instantáneas"
  - "conjuntos de registros, instantáneas"
  - "instantáneas"
  - "instantáneas, compatibilidad de ODBC"
  - "cursores estáticos"
ms.assetid: b5293a52-0657-43e9-bd71-fe3785b21c7e
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# Instant&#225;nea
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Una instantánea es un conjunto de registros que refleja una vista estática de los datos tal como eran en el momento en que se creó la instantánea.  Una vez que abre la instantánea y se desplaza por todos los registros, el conjunto de registros que contiene y sus valores no cambian hasta que se recompile la instantánea llamando a **Requery**.  
  
> [!NOTE]
>  Este tema es aplicable a las clases ODBC de MFC.  Si se están utilizando las clases DAO de MFC en lugar de las clases ODBC de MFC, vea [CDaoRecordset::Open](../Topic/CDaoRecordset::Open.md) para obtener una descripción de los conjuntos de registros de tipo instantánea.  
  
 Con las clases de base de datos se pueden crear instantáneas actualizables y de sólo lectura.  A diferencia de los conjuntos de registros dinámicos, las instantáneas actualizables no reflejan los cambios de los valores de registro efectuados por otros usuarios, pero sí reflejan las actualizaciones y eliminaciones llevadas a cabo por el programa.  Los registros agregados a una instantánea no son visibles para dicho objeto hasta que se llama a **Requery**.  
  
> [!TIP]
>  Una instantánea es un cursor estático de ODBC.  Los cursores estáticos no obtienen realmente una fila de datos hasta que el usuario no se desplaza al registro en cuestión.  Para garantizar que todos los registros se recuperan inmediatamente, el usuario puede desplazarse al final del conjunto de registros y, a continuación, al primer registro que desee ver.  No obstante, conviene señalar que el desplazamiento hasta el final implica una sobrecarga adicional y puede disminuir el rendimiento.  
  
 Las instantáneas son más útiles cuando se necesita que los datos permanezcan fijos durante las operaciones, así como cuando se genera un informe o se realizan cálculos.  Aun así, el origen de datos puede divergir considerablemente de la instantánea, por lo que será necesario recompilarla periódicamente.  
  
 La compatibilidad con las instantáneas se basa en la biblioteca de cursores ODBC, que proporciona cursores estáticos y actualizaciones con ubicación \(necesarios para la actualización\) para cualquier controlador de nivel 1.  La biblioteca de cursores DLL debe estar cargada en memoria para obtener dicha compatibilidad.  Cuando se crea un objeto `CDatabase` y se llama a la función miembro `OpenEx`, se debe especificar la opción **CDatabase::useCursorLib** del parámetro `dwOptions`.  Si se llama a la función miembro **Open**, la biblioteca de cursores se carga de forma predeterminada.  Si se están utilizando conjuntos de registros dinámicos en lugar de instantáneas, no hay que provocar la carga de la biblioteca de cursores.  
  
 Las instantáneas sólo están disponibles si la biblioteca de cursores ODBC se cargó cuando se creó el objeto `CDatabase` o si el controlador ODBC que se esté utilizando es compatible con los cursores estáticos.  
  
> [!NOTE]
>  En algunos controladores ODBC, puede que las instantáneas \(cursores estáticos\) no sean actualizables.  Compruebe la documentación del controlador para saber los tipos de cursor que son compatibles y los tipos de simultaneidad que admiten.  Para que las instantáneas sean actualizables, asegúrese de cargar la biblioteca de cursores en memoria al crear un objeto `CDatabase`.  Para obtener más información, vea [ODBC: Biblioteca de cursores ODBC](../../data/odbc/odbc-the-odbc-cursor-library.md).  
  
> [!NOTE]
>  Si se desea utilizar tanto instantáneas como conjuntos de registros dinámicos, se debe basar en dos objetos `CDatabase` distintos \(dos conexiones distintas\).  
  
 Para obtener más información sobre las propiedades que las instantáneas comparten con todos los conjuntos de registros, vea [Conjunto de registros \(ODBC\)](../../data/odbc/recordset-odbc.md).  Para obtener más información sobre ODBC y las instantáneas, incluida la biblioteca de cursores ODBC, vea [ODBC](../../data/odbc/odbc-basics.md).  
  
## Vea también  
 [Conectividad abierta de bases de datos \(ODBC\)](../../data/odbc/open-database-connectivity-odbc.md)