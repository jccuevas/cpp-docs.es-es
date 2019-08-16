---
title: Asignación y liberación de memoria para un BSTR
ms.date: 11/04/2016
f1_keywords:
- bstr
helpviewer_keywords:
- BSTRs, memory allocation
- memory deallocation, string memory
- memory [C++], releasing
- memory allocation, BSTRs
- memory deallocation, BSTR memory
- strings [C++], releasing
ms.assetid: 98041e29-3442-4a02-b425-7a4a13e9cc84
ms.openlocfilehash: a7a82acff959d18dcadd3a2c8516a20d60a617d3
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69491408"
---
# <a name="allocating-and-releasing-memory-for-a-bstr"></a>Asignación y liberación de memoria para un BSTR

Cuando crea `BSTR`s y los pasa entre objetos com, debe tener cuidado al tratar la memoria que usan para evitar pérdidas de memoria. Cuando un `BSTR` permanece dentro de una interfaz, debe liberar su memoria cuando haya terminado. Sin embargo, cuando `BSTR` una pasa de una interfaz, el objeto receptor asume la responsabilidad de su administración de memoria.

En general, las reglas para asignar y liberar memoria asignada `BSTR`para s son las siguientes:

- Cuando se llama a una función que espera un `BSTR` argumento, se debe asignar la memoria `BSTR` para antes de la llamada y liberarla posteriormente. Por ejemplo:

   [!code-cpp[NVC_ATLMFC_Utilities#192](../atl-mfc-shared/codesnippet/cpp/allocating-and-releasing-memory-for-a-bstr_1.cpp)]

   [!code-cpp[NVC_ATLMFC_Utilities#193](../atl-mfc-shared/codesnippet/cpp/allocating-and-releasing-memory-for-a-bstr_2.cpp)]

- Cuando se llama a una función que devuelve un `BSTR`, se debe liberar la cadena. Por ejemplo:

   [!code-cpp[NVC_ATLMFC_Utilities#194](../atl-mfc-shared/codesnippet/cpp/allocating-and-releasing-memory-for-a-bstr_3.cpp)]

   [!code-cpp[NVC_ATLMFC_Utilities#195](../atl-mfc-shared/codesnippet/cpp/allocating-and-releasing-memory-for-a-bstr_4.cpp)]

- Cuando implemente una función que devuelva `BSTR`un, asigne la cadena pero no la libere. Que recibe la función libera la memoria. Por ejemplo:

   [!code-cpp[NVC_ATLMFC_Utilities#196](../atl-mfc-shared/codesnippet/cpp/allocating-and-releasing-memory-for-a-bstr_5.cpp)]

## <a name="see-also"></a>Vea también

[Cadenas (ATL/MFC)](../atl-mfc-shared/strings-atl-mfc.md)<br/>
[CStringT::AllocSysString](../atl-mfc-shared/reference/cstringt-class.md#allocsysstring)<br/>
[SysAllocString](/windows/win32/api/oleauto/nf-oleauto-sysallocstring)<br/>
[SysFreeString](/windows/win32/api/oleauto/nf-oleauto-sysfreestring)
