---
title: Requisitos del controlador ODBC para conjuntos de registros dinámicos | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- ODBC recordsets, dynasets
- drivers, for dynasets
- drivers, ODBC
- recordsets, dynasets
- dynasets
- ODBC drivers, dynasets
ms.assetid: 585cc67b-4d92-404b-9903-d769cd17badc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: d9fad26440cea2c8ec2efd7d07dacb83547252e3
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33089238"
---
# <a name="odbc-driver-requirements-for-dynasets"></a>Requisitos del controlador ODBC para conjuntos de registros dinámicos
En las clases de base de datos ODBC de MFC, conjuntos de registros dinámicos son conjuntos de registros con propiedades dinámicas; permanecen sincronizados con el origen de datos de ciertas formas. Conjuntos de registros dinámicos MFC (pero no sea de sólo avance de conjuntos de registros) necesitan un controlador ODBC compatible con la API de nivel 2. Si el controlador para el [origen de datos](../../data/odbc/data-source-odbc.md) se ajusta a la API de nivel 1 conjunto, puede seguir utilizar tanto instantáneas actualizables y de sólo lectura y conjuntos de registros solo hacia delante, pero no los dynasets. Sin embargo, un controlador de nivel 1 puede admitir conjuntos de registros dinámicos si admite obtención extendida y cursores dinámicos.  
  
 En la terminología ODBC, conjuntos de registros dinámicos y las instantáneas se denominan cursores. Un cursor es un mecanismo utilizado para realizar el seguimiento de su posición en un conjunto de registros. Para obtener más información sobre los requisitos del controlador para conjuntos de registros dinámicos, vea [Dynaset](../../data/odbc/dynaset.md). Para obtener más información acerca de los cursores, vea el [Open Database Connectivity (ODBC)](https://msdn.microsoft.com/en-us/library/ms710252.aspx) SDK en la documentación de MSDN.  
  
> [!NOTE]
>  Para conjuntos de registros actualizables, el controlador ODBC debe admitir instrucciones de actualización por posición o el **:: SQLSetPos** función de la API de ODBC. Si se admiten ambas, MFC utiliza **:: SQLSetPos** para mejorar la eficacia. O bien, para las instantáneas, puede usar la biblioteca de cursores, que proporciona la compatibilidad requerida para las instantáneas actualizables (cursores estáticos y las instrucciones update posicionadas).  
  
## <a name="see-also"></a>Vea también  
 [Conceptos básicos de ODBC](../../data/odbc/odbc-basics.md)