---
title: IUnknown
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- COM interfaces, base interface
- IUnknown interface
ms.assetid: e6b85472-e54b-4b8c-b19f-4454d6c05a8f
ms.openlocfilehash: 9c9faa4cffcdc8e6840dfbbe141cb63f51155ded
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69492071"
---
# <a name="iunknown"></a>IUnknown

[IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) es la interfaz base de todas las demás interfaces com.  Esta interfaz define tres métodos: [QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q_)), [AddRef](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref)y [Release](/windows/win32/api/unknwn/nf-unknwn-iunknown-release). [QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q_)) permite a un usuario de la interfaz solicitar al objeto un puntero a otra de sus interfaces. [AddRef](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref) y [Release](/windows/win32/api/unknwn/nf-unknwn-iunknown-release) implementan el recuento de referencias en la interfaz.

## <a name="see-also"></a>Vea también

[Introducción a COM](../atl/introduction-to-com.md)<br/>
[IUnknown y herencia de interfaz](/windows/win32/com/iunknown-and-interface-inheritance)
