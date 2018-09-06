---
title: Recomendaciones para elegir entre ATL y MFC | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC, ATL support
- ATL, vs. MFC
ms.assetid: 269325bb-11a8-4330-ad2b-a14a2458679e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0a9bbf30c728b6562da0c56c25b177697f0882a5
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/05/2018
ms.locfileid: "43762130"
---
# <a name="recommendations-for-choosing-between-atl-and-mfc"></a>Recomendaciones para elegir entre ATL y MFC

Al desarrollar aplicaciones y componentes, puede elegir entre dos enfoques, ATL y MFC (la biblioteca Microsoft Foundation Class).

## <a name="using-atl"></a>Uso de ATL

ATL es una forma rápida y fácil para crear un componente COM en C++ y mantener una superficie pequeña. Usar ATL para crear un control si no necesita toda la funcionalidad integrada que MFC proporciona automáticamente.

## <a name="using-mfc"></a>Uso de MFC

MFC permite crear aplicaciones completas, controles ActiveX y documentos activos. Si ya ha creado un control con MFC, puede continuar el desarrollo en MFC. Al crear un nuevo control, considere el uso de ATL si no necesita toda la funcionalidad integrada de MFC.

## <a name="using-atl-in-an-mfc-project"></a>Uso de ATL en un proyecto MFC

Puede agregar compatibilidad con ATL a un proyecto MFC existente mediante la ejecución de un asistente. Para obtener más información, consulte [agregar compatibilidad con ATL a un proyecto MFC](../mfc/reference/adding-atl-support-to-your-mfc-project.md).

## <a name="see-also"></a>Vea también

[Introducción a ATL](../atl/introduction-to-atl.md)

