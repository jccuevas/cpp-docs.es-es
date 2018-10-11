---
title: Requisitos del controlador ODBC para conjuntos de registros dinámicos | Microsoft Docs
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
ms.openlocfilehash: f6c7a9282ce1516ae3410307b74a66ba34adbcea
ms.sourcegitcommit: 3a141cf07b5411d5f1fdf6cf67c4ce928cf389c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/11/2018
ms.locfileid: "49082714"
---
# <a name="odbc-driver-requirements-for-dynasets"></a>Requisitos del controlador ODBC para conjuntos de registros dinámicos

En las clases de base de datos ODBC de MFC, conjuntos de registros dinámicos son conjuntos de registros con propiedades dinámicas; permanecen sincronizados con el origen de datos de determinadas maneras. Conjuntos de registros dinámicos MFC (pero no sólo hacia delante) necesita un controlador ODBC compatible con la API de nivel 2. Si el controlador para su [origen de datos](../../data/odbc/data-source-odbc.md) se ajusta a la API de nivel 1 se establece, se pueden seguir utilizando tanto instantáneas actualizables y de solo lectura y conjuntos de registros solo hacia delante, pero no los dynasets. Sin embargo, un controlador de nivel 1 puede admitir conjuntos de registros dinámicos si admite obtención extendida y los cursores dinámicos.  
  
En la terminología ODBC, conjuntos de registros dinámicos y las instantáneas se denominan cursores. Un cursor es un mecanismo utilizado para realizar el seguimiento de su posición en un conjunto de registros. Para obtener más información sobre los requisitos del controlador para conjuntos de registros dinámicos, vea [Dynaset](../../data/odbc/dynaset.md). Para obtener más información acerca de los cursores, vea el [Open Database Connectivity (ODBC)](/previous-versions/windows/desktop/ms710252) SDK en la documentación de MSDN.  
  
> [!NOTE]
>  Para conjuntos de registros actualizables, el controlador ODBC debe admitir instrucciones de actualización por posición o el `::SQLSetPos` función de la API de ODBC. Si se admiten ambas, MFC utiliza `::SQLSetPos` para mejorar la eficacia. Como alternativa, las instantáneas, puede usar la biblioteca de cursores, que proporciona la compatibilidad necesaria para las instantáneas actualizables (cursores estáticos y las instrucciones update posicionadas).  
  
## <a name="see-also"></a>Vea también  

[Conceptos básicos de ODBC](../../data/odbc/odbc-basics.md)