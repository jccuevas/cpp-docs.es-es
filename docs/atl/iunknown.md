---
title: IDesconocido
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- COM interfaces, base interface
- IUnknown interface
ms.assetid: e6b85472-e54b-4b8c-b19f-4454d6c05a8f
ms.openlocfilehash: 6adfbdc59b2a63aa2f2bb39e27139ca977ba9465
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/20/2019
ms.locfileid: "75298758"
---
# <a name="iunknown"></a>IDesconocido

[IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) es la interfaz base de todas las demás interfaces com.  Esta interfaz define tres métodos: [QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q)), [AddRef](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref)y [Release](/windows/win32/api/unknwn/nf-unknwn-iunknown-release). [QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q)) permite a un usuario de la interfaz solicitar al objeto un puntero a otra de sus interfaces. [AddRef](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref) y [Release](/windows/win32/api/unknwn/nf-unknwn-iunknown-release) implementan el recuento de referencias en la interfaz.

## <a name="see-also"></a>Vea también

[Introducción a COM](../atl/introduction-to-com.md)<br/>
[IUnknown y herencia de interfaz](/windows/win32/com/iunknown-and-interface-inheritance)
