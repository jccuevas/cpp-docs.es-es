---
title: Requisitos de atributo | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
ms.assetid: e42ca06f-5f3c-40b5-972a-39ecf522d227
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: ea84b46e31d57ec05bf9641674d045f531b04722
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "42593757"
---
# <a name="attribute-requirements"></a>Requisitos de los atributos
Los requisitos de atributos de C++ describen los tipos de proyecto, configuración del compilador y demás información necesaria para un atributo para que funcione. A continuación se describen las categorías de información.
  
> [!NOTE]
> No se admite el uso de atributos en una clase que deriva de una clase que también utiliza atributos.
  
## <a name="header"></a>Header
 Este campo enumera los archivos de encabezado que se deben incluidos, antes de que se puede usar un atributo.
  
## <a name="project"></a>Proyecto
 Este campo describe los tipos de proyecto en el que se puede usar un atributo.
  
## <a name="compiler"></a>Compilador
 Este campo proporciona las opciones del compilador que deben estar presentes para este atributo se usará.
  
## <a name="see-also"></a>Vea también
 [Contextos de atributos](../windows/attribute-contexts.md)  
 [Atributos por grupo](../windows/attributes-by-group.md)