---
title: Tipos de valor y su comportamiento (C++ / c++ / CLI) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- value types
ms.assetid: 5cb872a6-1e0a-429d-853d-df4ab47e8f2a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 4d2d980e48a6f948c35faf0c4e42969795ef8dc7
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46404662"
---
# <a name="value-types-and-their-behaviors-ccli"></a>Tipos de valor y su comportamiento (C++/CLI)

Tipos de valor han cambiado de distintas maneras de extensiones administradas para C++ a Visual C++. En esta sección, nos centramos en el tipo de enumeración CLR y el tipo de clase de valor, junto con la conversión boxing y acceso a la instancia de conversión boxing al montón CLR, así como de los punteros interiores y anclados. Ha habido muchos cambios de lenguaje en esta área.

## <a name="in-this-section"></a>En esta sección

[Tipo de enumeración de CLR](../dotnet/value-types-and-their-behaviors-cpp-cli.md)<br/>
Describe los cambios en la declaración y el comportamiento de las enumeraciones.

[Conversión boxing implícita de los tipos de valor](../dotnet/implicit-boxing-of-value-types.md)<br/>
Explica la motivación para la conversión boxing implícita de tipos de valor y los cambios de comportamiento consecutivas.

[Controlador de seguimiento de un valor al que se le ha aplicado la conversión boxing](../dotnet/a-tracking-handle-to-a-boxed-value.md)<br/>
Describe la conversión boxing de forma implícita del valor de tipos se traduce en un identificador de seguimiento para el objeto de valor con conversión boxing.

[Semántica de los tipos de valor](../dotnet/value-type-semantics.md)<br/>
Describe los cambios en la semántica de tipos de valor, incluidos los métodos virtuales heredados, los constructores predeterminados de clase, punteros interiores y punteros anclados.

## <a name="see-also"></a>Vea también

[Manual de migraciones C++/CLI](../dotnet/cpp-cli-migration-primer.md)<br/>
[Clases y structs](../windows/classes-and-structs-cpp-component-extensions.md)