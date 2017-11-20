---
title: Recomendaciones para elegir entre ATL y MFC | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- MFC, ATL support
- ATL, vs. MFC
ms.assetid: 269325bb-11a8-4330-ad2b-a14a2458679e
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: d912c6cd997c23b9623d20a104327fb6e4701494
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="recommendations-for-choosing-between-atl-and-mfc"></a>Recomendaciones para elegir entre ATL y MFC
Al desarrollar aplicaciones y componentes, puede elegir entre dos enfoques: ATL y MFC (la biblioteca Microsoft Foundation Class).  
  
## <a name="using-atl"></a>Con ATL  
 ATL es una forma rápida y sencilla para crear un componente COM en C++ y mantener una pequeña superficie. Utilice ATL para crear un control si no necesita toda la funcionalidad integrada que MFC proporciona automáticamente.  
  
## <a name="using-mfc"></a>Uso de MFC  
 MFC permite crear aplicaciones completas, controles ActiveX y documentos activos. Si ya ha creado un control con MFC, puede continuar el desarrollo en MFC. Al crear un nuevo control, considere el uso de ATL si no necesita toda la funcionalidad integrada de MFC.  
  
## <a name="using-atl-in-an-mfc-project"></a>Uso de ATL en un proyecto MFC  
 Puede agregar compatibilidad con ATL a un proyecto MFC existente mediante la ejecución de un asistente. Para obtener más información, consulte [agregar compatibilidad con ATL a un proyecto MFC](../mfc/reference/adding-atl-support-to-your-mfc-project.md).  
  
## <a name="see-also"></a>Vea también  
 [Introducción a ATL](../atl/introduction-to-atl.md)

