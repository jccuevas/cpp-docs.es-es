---
title: API ANSI en desuso | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC, ANSI deprecated methods
ms.assetid: c7c5a6fd-95e4-4bee-b3d5-d3826c30947d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7e989b6f2193142de8feb4124e365285957ee804
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46439873"
---
# <a name="deprecated-ansi-apis"></a>API ANSI en desuso

La biblioteca Microsoft Foundation Class (MFC) es la migración hacia las clases y métodos que se basan en el juego de caracteres Unicode. Por lo tanto, las versiones ANSI de varios métodos MFC están en desuso. Use las versiones Unicode de estos métodos en sus aplicaciones futuras.

Comenzando con la versión de los controles comunes de Windows 6.1, que se distribuye con Windows Vista, los siguientes métodos de ANSI están en desuso.

## <a name="cbutton-class"></a>CButton (clase)

```
AFX_ANSI_DEPRECATED BOOL GetIdealSize(LPSIZE psize) const;


AFX_ANSI_DEPRECATED BOOL GetImageList(PBUTTON_IMAGELIST pbuttonImagelist) const;


AFX_ANSI_DEPRECATED BOOL GetTextMargin(LPRECT pmargin) const;


AFX_ANSI_DEPRECATED BOOL SetImageList(PBUTTON_IMAGELIST pbuttonImagelist);

AFX_ANSI_DEPRECATED BOOL SetTextMargin(LPRECT pmargin);
```

## <a name="ccomboboxex-class"></a>CComboBoxEx (clase)

```
AFX_ANSI_DEPRECATED HRESULT SetWindowTheme(LPCWSTR pszSubAppName);
```

## <a name="cedit-class"></a>CEdit (clase)

```
AFX_ANSI_DEPRECATED BOOL GetCueBanner(LPWSTR lpszText,
    int cchText) const;


AFX_ANSI_DEPRECATED BOOL SetCueBanner(LPCWSTR lpszText,
    BOOL fDrawIfFocused = FALSE);
```

## <a name="clinkctrl-class"></a>CLinkCtrl (clase)

Toda la clase está en desuso.

## <a name="clistctrl-class"></a>CListCtrl (clase)

```
AFX_ANSI_DEPRECATED void CancelEditLabel();

AFX_ANSI_DEPRECATED int EnableGroupView(BOOL fEnable);

AFX_ANSI_DEPRECATED int GetGroupInfo(int iGroupId,
    PLVGROUP pgrp) const;


AFX_ANSI_DEPRECATED void GetGroupMetrics(PLVGROUPMETRICS pGroupMetrics) const;


AFX_ANSI_DEPRECATED BOOL GetInsertMark(LPLVINSERTMARK lvim) const;


AFX_ANSI_DEPRECATED COLORREF GetInsertMarkColor() const;


AFX_ANSI_DEPRECATED int GetInsertMarkRect(LPRECT pRect) const;


AFX_ANSI_DEPRECATED COLORREF GetOutlineColor() const;


AFX_ANSI_DEPRECATED UINT GetSelectedColumn() const;


AFX_ANSI_DEPRECATED BOOL GetTileInfo(PLVTILEINFO pti) const;


AFX_ANSI_DEPRECATED BOOL GetTileViewInfo(PLVTILEVIEWINFO ptvi) const;


AFX_ANSI_DEPRECATED DWORD GetView() const;


AFX_ANSI_DEPRECATED BOOL HasGroup(int iGroupId) const;


AFX_ANSI_DEPRECATED int InsertGroup(int index,
    PLVGROUP pgrp);

AFX_ANSI_DEPRECATED void InsertGroupSorted(PLVINSERTGROUPSORTED pStructInsert);

AFX_ANSI_DEPRECATED int InsertMarkHitTest(LPPOINT pPoint,
    LPLVINSERTMARK lvim) const;


AFX_ANSI_DEPRECATED BOOL IsGroupViewEnabled() const;


AFX_ANSI_DEPRECATED void MoveGroup(int iGroupId,
    int toIndex);

AFX_ANSI_DEPRECATED void MoveItemToGroup(int idItemFrom,
    int idGroupTo);

AFX_ANSI_DEPRECATED void RemoveAllGroups();

AFX_ANSI_DEPRECATED int RemoveGroup(int iGroupId);

AFX_ANSI_DEPRECATED BOOL SetGroupInfo(int iGroupId,
    PLVGROUP pGroup);

AFX_ANSI_DEPRECATED void SetGroupMetrics(PLVGROUPMETRICS pGroupMetrics);

AFX_ANSI_DEPRECATED BOOL SetInfoTip(PLVSETINFOTIP plvInfoTip);

AFX_ANSI_DEPRECATED BOOL SetInsertMark(LPLVINSERTMARK lvim);

AFX_ANSI_DEPRECATED COLORREF SetInsertMarkColor(COLORREF color);

AFX_ANSI_DEPRECATED COLORREF SetOutlineColor(COLORREF color);

AFX_ANSI_DEPRECATED void SetSelectedColumn(int iCol);

AFX_ANSI_DEPRECATED BOOL SetTileInfo(PLVTILEINFO pti);

AFX_ANSI_DEPRECATED BOOL SetTileViewInfo(PLVTILEVIEWINFO ptvi);

AFX_ANSI_DEPRECATED DWORD SetView(int iView);

AFX_ANSI_DEPRECATED BOOL SortGroups(PFNLVGROUPCOMPARE _pfnGroupCompare,
    LPVOID _plv);
```

## <a name="crebarctrl-class"></a>CReBarCtrl (clase)

```
AFX_ANSI_DEPRECATED void GetBandMargins(PMARGINS pMargins) const;


AFX_ANSI_DEPRECATED HRESULT SetWindowTheme(LPCWSTR pszSubAppName);
```

## <a name="ctoolbarctrl-class"></a>CToolBarCtrl (clase)

```
AFX_ANSI_DEPRECATED void GetMetrics(LPTBMETRICS ptbm) const;


AFX_ANSI_DEPRECATED void SetMetrics(LPTBMETRICS ptbm);

AFX_ANSI_DEPRECATED HRESULT SetWindowTheme(LPCWSTR pszSubAppName);
```

## <a name="ctooltipctrl-class"></a>CToolTipCtrl (clase)

```
AFX_ANSI_DEPRECATED HRESULT SetWindowTheme(LPCWSTR pszSubAppName);
```

## <a name="see-also"></a>Vea también

[Requisitos de compilación para los controles comunes de Windows Vista](../mfc/build-requirements-for-windows-vista-common-controls.md)

