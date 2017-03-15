---
title: "Conjunto de registros: Volver a consultar un conjunto de registros (ODBC) | Microsoft Docs"
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
  - "conjuntos de registros ODBC, volver a consultar"
  - "conjuntos de registros, volver a consultar"
  - "actualizar conjuntos de registros"
  - "Requery (método)"
  - "volver a consultar conjuntos de registros"
ms.assetid: 4ebc3b5b-5b91-4f51-a967-245223c6b8e1
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# Conjunto de registros: Volver a consultar un conjunto de registros (ODBC)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Este tema es aplicable a las clases ODBC de MFC.  
  
 Este tema explica cómo utilizar un objeto de conjunto de registros para realizar una nueva consulta sobre sí mismo \(es decir, actualizarse\) en la base de datos y cuándo puede resultar conveniente hacerlo mediante la función miembro [Requery](../Topic/CRecordset::Requery.md).  
  
 Las principales razones para realizar una nueva consulta a un conjunto de registros son:  
  
-   Actualizar el conjunto de registros respecto a los registros agregados por el propio usuario o por otros usuarios y los registros eliminados por estos últimos \(los que elimine ya aparecen reflejados en el conjunto de registros\).  
  
-   Actualizar el conjunto de registros a partir de los valores de parámetro modificados.  
  
##  <a name="_core_bringing_the_recordset_up_to_date"></a> Actualizar el conjunto de registros  
 Con frecuencia, es conveniente realizar una nueva consulta al objeto de conjunto de registros para actualizarlo.  En un entorno de base de datos de varios usuarios, otros usuarios pueden realizar cambios en los datos durante la vida útil del conjunto de registros.  Para obtener más información sobre cuándo refleja un conjunto de registros los cambios realizados por otros usuarios y cuándo reflejan sus cambios los conjuntos de registros de los demás usuarios, vea [Conjunto de registros: Actualizar los registros \(ODBC\)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md) y [Conjunto de registros dinámicos](../../data/odbc/dynaset.md).  
  
##  <a name="_core_requerying_based_on_new_parameters"></a> Realizar una nueva consulta basada en nuevos parámetros  
 Otro uso frecuente \(e igualmente importante\) de [Requery](../Topic/CRecordset::Requery.md) consiste en seleccionar un nuevo conjunto de registros basado en valores de parámetros modificados.  
  
> [!TIP]
>  La velocidad de consulta es probablemente mucho más rápida si se llama a **Requery** con valores de parámetro diferentes que si se llama de nuevo a **Open**.  
  
##  <a name="_core_requerying_dynasets_vs.._snapshots"></a> Realizar una nueva consulta en conjuntos de instantáneas  
 Debido a que los conjuntos de registros dinámicos están diseñados para mostrar un conjunto de registros con datos dinámicos y actualizados, a menudo es conveniente realizar una nueva consulta en éstos para reflejar la inclusión de otros usuarios.  Las instantáneas, en cambio, son útiles porque se puede confiar en su contenido estático a la hora de preparar informes, calcular totales, etc.  Sin embargo, a veces puede ser conveniente realizar también una nueva consulta en una instantánea.  En entornos multiusuario, los datos de instantáneas pueden perder la sincronización con el origen de datos a medida que otros usuarios modifican la base de datos.  
  
#### Para realizar una nueva consulta a un objeto de conjunto de registros  
  
1.  Llame a la función miembro [Requery](../Topic/CRecordset::Requery.md) del objeto.  
  
 Como alternativa, se puede cerrar y volver abrir el conjunto de registros original.  En cualquier caso, el nuevo conjunto de registros representa el estado actual del origen de datos.  
  
 Por ejemplo, vea [Vistas de registros: Llenar un cuadro de lista con datos de otro conjunto de registros](../../data/filling-a-list-box-from-a-second-recordset-mfc-data-access.md).  
  
> [!TIP]
>  Para optimizar el rendimiento de **Requery**, evite modificar el [filtro](../../data/odbc/recordset-filtering-records-odbc.md) o la [ordenación](../../data/odbc/recordset-sorting-records-odbc.md) del conjunto de registros.  Cambie sólo el valor del parámetro antes de llamar a **Requery**.  
  
 Si se produce un error en la llamada a **Requery**, puede volver a intentarlo. De lo contrario, se cerrará la aplicación.  Puede ocurrir un error en la llamada a **Requery** o a **Open** por varias razones:  puede ocurrir un error de red; o, durante la llamada, otro usuario puede obtener acceso exclusivo después de liberarse los datos existentes pero antes de obtener nuevos datos, o puede haberse eliminado la tabla de la que depende el conjunto de registros.  
  
## Vea también  
 [Conjunto de registros \(ODBC\)](../../data/odbc/recordset-odbc.md)   
 [Conjunto de registros: Enlazar dinámicamente columnas de datos \(ODBC\)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)   
 [Conjunto de registros: Crear y cerrar conjuntos de registros \(ODBC\)](../../data/odbc/recordset-creating-and-closing-recordsets-odbc.md)