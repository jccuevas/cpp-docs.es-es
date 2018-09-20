---
title: Declaraciones de miembros en una clase o interfaz (C++ / c++ / CLI) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- members, declaration syntax
- class members, declaration syntax
ms.assetid: 95d312a4-198b-46f0-b8f5-15253807c55e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 80b872b4c614677c05b0d28b821d3a48255905c5
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46430644"
---
# <a name="member-declarations-within-a-class-or-interface-ccli"></a>Declaraciones de miembros en una clase o interfaz (C++/CLI)

La declaración de propiedades y operadores se ha reformado ampliamente de extensiones administradas para C++ a Visual C++, ocultando los detalles de implementación subyacente que se mostraban en el diseño de extensiones administradas. También se han modificado las declaraciones de eventos.

En la categoría de los cambios se ha introducido que no admite extensiones administradas, los constructores estáticos pueden ahora ser definido fuera de línea (era necesario para que pueda definir mediante inserción en extensiones administradas) y la noción de un constructor de delegación.

## <a name="in-this-section"></a>En esta sección

[Declaración de propiedades](../dotnet/property-declaration.md)<br/>
Describe los cambios realizados en las declaraciones de propiedad.

[Declaración de índices de propiedad](../dotnet/property-index-declaration.md)<br/>
Describe los cambios realizados en las declaraciones de propiedad indizada.

[Delegados y eventos](../dotnet/delegates-and-events.md)<br/>
Describe los cambios realizados en la sintaxis para declarar los delegados y eventos.

[Sellar una función virtual](../dotnet/sealing-a-virtual-function.md)<br/>
Describe los cambios realizados en la sintaxis para sellar una función.

[Operadores sobrecargados](../dotnet/overloaded-operators.md)<br/>
Describe los cambios realizados en la sobrecarga de operadores.

[Cambios en los operadores de conversión](../dotnet/changes-to-conversion-operators.md)<br/>
Describe los cambios realizados en los operadores de conversión.

[Reemplazo explícito de un miembro de interfaz](../dotnet/explicit-override-of-an-interface-member.md)<br/>
Describe los cambios realizados en el método para reemplazar explícitamente un miembro de interfaz.

[Funciones virtuales privadas](../dotnet/private-virtual-functions.md)<br/>
Describe los cambios de la manera en que se controlan las funciones virtuales privadas en clases derivadas.

[La vinculación de miembros integrales const estáticos ya no es literal](../dotnet/static-const-int-linkage-is-no-longer-literal.md)<br/>
Describe los cambios de la manera `static const` están vinculados a los miembros enteros y cómo declarar explícitamente una constante con el nuevo `literal` palabra clave.

## <a name="see-also"></a>Vea también

[Manual de migraciones C++/CLI](../dotnet/cpp-cli-migration-primer.md)