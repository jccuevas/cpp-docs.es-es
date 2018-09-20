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
ms.openlocfilehash: 0aa52f77403602d7f63f39b19e05186a9cea7c9d
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46424678"
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

[Contextos de atributos](../windows/attribute-contexts.md)<br/>
[Atributos por grupo](../windows/attributes-by-group.md)