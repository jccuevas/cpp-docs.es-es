---
title: "Requisitos del controlador ODBC para conjuntos de registros din&#225;micos | Microsoft Docs"
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
  - "controladores, para conjuntos de registros dinámicos"
  - "controladores, ODBC"
  - "conjuntos de registros dinámicos"
  - "controladores ODBC, conjuntos de registros dinámicos"
  - "conjuntos de registros ODBC, conjuntos de registros dinámicos"
  - "conjuntos de registros, conjuntos de registros dinámicos"
ms.assetid: 585cc67b-4d92-404b-9903-d769cd17badc
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Requisitos del controlador ODBC para conjuntos de registros din&#225;micos
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

En las clases de base de datos ODBC de MFC, los conjuntos de registros dinámicos son conjuntos de registros con propiedades dinámicas; permanecen sincronizados con el origen de datos de determinadas maneras.  Los conjuntos de registros dinámicos de MFC \(pero no los conjuntos de registros sólo hacia delante\) necesitan un controlador ODBC que sea compatible con la API de nivel 2.  Si el controlador del [origen de datos](../../data/odbc/data-source-odbc.md) es compatible con la API de nivel 1, se pueden seguir utilizando tanto instantáneas actualizables y de sólo lectura como conjuntos de registros sólo hacia delante, pero no conjuntos de registros dinámicos.  No obstante, un controlador de nivel 1 puede admitir conjuntos de registros dinámicos si admite obtención extendida y cursores dirigidos por conjuntos de claves.  
  
 En terminología ODBC, los conjuntos de registros dinámicos y las instantáneas se denominan cursores.  Un cursor es un mecanismo utilizado para mantener el seguimiento de su posición en un conjunto de registros.  Para obtener más información sobre los requisitos de controladores para los conjuntos de registros dinámicos, vea [Conjunto de registros dinámicos](../../data/odbc/dynaset.md).  Para obtener más información sobre cursores, vea el SDK de [Conectividad abierta de bases de datos \(ODBC\)](https://msdn.microsoft.com/en-us/library/ms710252.aspx) en la documentación de MSDN.  
  
> [!NOTE]
>  Para los conjuntos de registros actualizables, el controlador ODBC debe admitir instrucciones de actualización con ubicación o la función de la API de ODBC **::SQLSetPos**.  Si se admiten ambas, MFC utiliza **::SQLSetPos** porque es más eficaz.  De forma alternativa, para las instantáneas, se puede utilizar la biblioteca de cursores, que proporciona la compatibilidad requerida para las instantáneas actualizables \(cursores estáticos e instrucciones de actualización con ubicación\).  
  
## Vea también  
 [Conceptos básicos de ODBC](../../data/odbc/odbc-basics.md)