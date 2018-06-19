---
title: Las herramientas del vinculador LNK1000 Error | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1000
dev_langs:
- C++
helpviewer_keywords:
- LNK1000
ms.assetid: 86421b9a-460a-4285-8dce-9b8257d78122
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2f67df9c53b79fabfc9559380b5b57a72e64cb8a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33298241"
---
# <a name="linker-tools-error-lnk1000"></a>Error de las herramientas del vinculador LNK1000
error desconocido; Consulte la documentación para opciones de soporte técnico  
  
 Anote las circunstancias del error, intente aislar el problema y crear un caso de prueba reproducible, a continuación, póngase en contacto con `Microsoft Product Support Services`. Para obtener información sobre cómo investigar y notificar estos errores, vea [ http://support.microsoft.com/default.aspx?scid=kb; en-us; 134650](http://support.microsoft.com/default.aspx?scid=kb;en-us;134650).  
  
 Puede obtener este error si mezcla archivos de encabezado estándar (por ejemplo, dos.h) y sus propios archivos. `#include` los encabezados estándar en primer lugar, seguido de sus propios archivos de encabezado.