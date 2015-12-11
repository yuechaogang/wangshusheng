# wangshusheng
#图书管理系统
// LibraryDlg.cpp : implementation file
//
12月9号代码
#include "stdafx.h"
#include "Library.h"
#include "LibraryDlg.h"
#include "BookDlg.h"
#include "ReaderDlg.h"
#include "BorrowDlg.h"
#include "ReturnDlg.h"

#ifdef _DEBUG
#define new DEBUG_NEW
#undef THIS_FILE
static char THIS_FILE[] = __FILE__;
#endif

/////////////////////////////////////////////////////////////////////////////
// CAboutDlg dialog used for App About

class CAboutDlg : public CDialog
{
public:
	CAboutDlg();

// Dialog Data
	//{{AFX_DATA(CAboutDlg)
	enum { IDD = IDD_ABOUTBOX };
	//}}AFX_DATA

	// ClassWizard generated virtual function overrides
	//{{AFX_VIRTUAL(CAboutDlg)
	protected:
	virtual void DoDataExchange(CDataExchange* pDX);    // DDX/DDV support
	//}}AFX_VIRTUAL

// Implementation
protected:
	//{{AFX_MSG(CAboutDlg)
	//}}AFX_MSG
	DECLARE_MESSAGE_MAP()
};

CAboutDlg::CAboutDlg() : CDialog(CAboutDlg::IDD)
{
	//{{AFX_DATA_INIT(CAboutDlg)
	//}}AFX_DATA_INIT
}

void CAboutDlg::DoDataExchange(CDataExchange* pDX)
{
	CDialog::DoDataExchange(pDX);
	//{{AFX_DATA_MAP(CAboutDlg)
	//}}AFX_DATA_MAP
}

BEGIN_MESSAGE_MAP(CAboutDlg, CDialog)
	//{{AFX_MSG_MAP(CAboutDlg)
		// No message handlers
	//}}AFX_MSG_MAP
END_MESSAGE_MAP()

/////////////////////////////////////////////////////////////////////////////
// CLibraryDlg dialog

CLibraryDlg::CLibraryDlg(CWnd* pParent /*=NULL*/)
	: CDialog(CLibraryDlg::IDD, pParent)
{
	//{{AFX_DATA_INIT(CLibraryDlg)
		// NOTE: the ClassWizard will add member initialization here
	//}}AFX_DATA_INIT
	// Note that LoadIcon does not require a subsequent DestroyIcon in Win32
	m_hIcon = AfxGetApp()->LoadIcon(IDR_MAINFRAME);
}

void CLibraryDlg::DoDataExchange(CDataExchange* pDX)
{
	CDialog::DoDataExchange(pDX);
	//{{AFX_DATA_MAP(CLibraryDlg)
		// NOTE: the ClassWizard will add DDX and DDV calls here
	//}}AFX_DATA_MAP
}

BEGIN_MESSAGE_MAP(CLibraryDlg, CDialog)
	//{{AFX_MSG_MAP(CLibraryDlg)
	ON_WM_SYSCOMMAND()
	ON_WM_PAINT()
	ON_WM_QUERYDRAGICON()
	ON_BN_CLICKED(IDC_BUTTON_GOODBYE, OnButtonGoodbye)
	ON_BN_CLICKED(IDC_BUTTON_BOOK, OnButtonBook)
	ON_BN_CLICKED(IDC_BUTTON_READER, OnButtonReader)
	ON_BN_CLICKED(IDC_BUTTON_BORROW, OnButtonBorrow)
	ON_BN_CLICKED(IDC_BUTTON_RETURN, OnButtonReturn)
	//}}AFX_MSG_MAP
END_MESSAGE_MAP()

/////////////////////////////////////////////////////////////////////////////
// CLibraryDlg message handlers

BOOL CLibraryDlg::OnInitDialog()
{
	CDialog::OnInitDialog();

	// Add "About..." menu item to system menu.

	// IDM_ABOUTBOX must be in the system command range.
	ASSERT((IDM_ABOUTBOX & 0xFFF0) == IDM_ABOUTBOX);
	ASSERT(IDM_ABOUTBOX < 0xF000);

	CMenu* pSysMenu = GetSystemMenu(FALSE);
	if (pSysMenu != NULL)
	{
		CString strAboutMenu;
		strAboutMenu.LoadString(IDS_ABOUTBOX);
		if (!strAboutMenu.IsEmpty())
		{
			pSysMenu->AppendMenu(MF_SEPARATOR);
			pSysMenu->AppendMenu(MF_STRING, IDM_ABOUTBOX, strAboutMenu);
		}
	}

	// Set the icon for this dialog.  The framework does this automatically
	//  when the application's main window is not a dialog
	SetIcon(m_hIcon, TRUE);			// Set big icon
	SetIcon(m_hIcon, FALSE);		// Set small icon
	
	// TODO: Add extra initialization here
	
	return TRUE;  // return TRUE  unless you set the focus to a control
}

void CLibraryDlg::OnSysCommand(UINT nID, LPARAM lParam)
{
	if ((nID & 0xFFF0) == IDM_ABOUTBOX)
	{
		CAboutDlg dlgAbout;
		dlgAbout.DoModal();
	}
	else
	{
		CDialog::OnSysCommand(nID, lParam);
	}
}

// If you add a minimize button to your dialog, you will need the code below
//  to draw the icon.  For MFC applications using the document/view model,
//  this is automatically done for you by the framework.

void CLibraryDlg::OnPaint() 
{
	if (IsIconic())
	{
		CPaintDC dc(this); // device context for painting

		SendMessage(WM_ICONERASEBKGND, (WPARAM) dc.GetSafeHdc(), 0);

		// Center icon in client rectangle
		int cxIcon = GetSystemMetrics(SM_CXICON);
		int cyIcon = GetSystemMetrics(SM_CYICON);
		CRect rect;
		GetClientRect(&rect);
		int x = (rect.Width() - cxIcon + 1) / 2;
		int y = (rect.Height() - cyIcon + 1) / 2;

		// Draw the icon
		dc.DrawIcon(x, y, m_hIcon);
	}
	else
	{
		CDialog::OnPaint();
	}
}

// The system calls this to obtain the cursor to display while the user drags
//  the minimized window.
HCURSOR CLibraryDlg::OnQueryDragIcon()
{
	return (HCURSOR) m_hIcon;
}

void CLibraryDlg::OnButtonGoodbye() 
{
	int nResponse=MessageBox("真得要离开吗?","退出提示",MB_YESNO);
	if(nResponse==IDYES)
	{
		OnOK();

	}
	else
	{
	}
	// TODO: Add your control notification handler code here
	
}

void CLibraryDlg::OnButtonBook() 
{
	CBookDlg dlg;
	dlg.DoModal();
	// TODO: Add your control notification handler code here
	
}

void CLibraryDlg::OnButtonReader() 
{
	CReaderDlg dlg;
	dlg.DoModal();
	// TODO: Add your control notification handler code here
	
}

void CLibraryDlg::OnButtonBorrow() 
{
	CBorrowDlg dlg;
	dlg.DoModal();
	// TODO: Add your control notification handler code here
	
}

void CLibraryDlg::OnButtonReturn() 
{
	CReturnDlg dlg;
	dlg.DoModal();
	// TODO: Add your control notification handler code here
	
}











#if !defined(AFX_BOOKDATASET_H__3F31D4F5_7B1A_4F48_886E_0BC189AC4148__INCLUDED_)
#define AFX_BOOKDATASET_H__3F31D4F5_7B1A_4F48_886E_0BC189AC4148__INCLUDED_

#if _MSC_VER > 1000
#pragma once
#endif // _MSC_VER > 1000
// BookDataSet.h : header file
//

/////////////////////////////////////////////////////////////////////////////
// CBookDataSet recordset

class CBookDataSet : public CRecordset
{
public:
	CBookDataSet(CDatabase* pDatabase = NULL);
	DECLARE_DYNAMIC(CBookDataSet)

// Field/Param Data
	//{{AFX_FIELD(CBookDataSet, CRecordset)
	CString	m_BOOK_ID;
	CString	m_BOOK_NAME;
	CString	m_AUTHOR;
	CString	m_PRESS;
	CString	m_PRESS_DATE;
	CString	m_FLAG_BORROW;
	//}}AFX_FIELD


// Overrides
	// ClassWizard generated virtual function overrides
	//{{AFX_VIRTUAL(CBookDataSet)
	public:
	virtual CString GetDefaultConnect();    // Default connection string
	virtual CString GetDefaultSQL();    // Default SQL for Recordset
	virtual void DoFieldExchange(CFieldExchange* pFX);  // RFX support
	//}}AFX_VIRTUAL

// Implementation
#ifdef _DEBUG
	virtual void AssertValid() const;
	virtual void Dump(CDumpContext& dc) const;
#endif
};

//{{AFX_INSERT_LOCATION}}
// Microsoft Visual C++ will insert additional declarations immediately before the previous line.

#endif // !defined(AFX_BOOKDATASET_H__3F31D4F5_7B1A_4F48_886E_0BC189AC4148__INCLUDED_)








12月10号代码
岳超刚
#if _MSC_VER > 1000
#pragma once
#endif // _MSC_VER > 1000
// BookDlg.h : header file
//

/////////////////////////////////////////////////////////////////////////////
// CBookDlg dialog
#include "BookDataSet.h"

class CBookDlg : public CDialog
{
// Construction
public:
	CBookDlg(CWnd* pParent = NULL);   // standard constructor
	BOOL SetButtonState();
	BOOL SetTextState();
	BOOL DisplayRecord();
	BOOL m_bEdit;
	BOOL m_bAdd;
	CBookDataSet m_rsDataSet;

// Dialog Data
	//{{AFX_DATA(CBookDlg)
	enum { IDD = IDD_DIALOG_BOOK };
	CString	m_strAuthor;
	CString	m_strBookID;
	CString	m_strBookIDQ;
	CString	m_strBookName;
	CString	m_strBookNameQ;
	CString	m_strFlag;
	CString	m_strPress;
	CString	m_strPressDate;
	//}}AFX_DATA


// Overrides
	// ClassWizard generated virtual function overrides
	//{{AFX_VIRTUAL(CBookDlg)
	protected:
	virtual void DoDataExchange(CDataExchange* pDX);    // DDX/DDV support
	//}}AFX_VIRTUAL

// Implementation
protected:

	// Generated message map functions
	//{{AFX_MSG(CBookDlg)
	afx_msg void OnCancelRec();
	afx_msg void OnDelete();
	afx_msg void OnEdit();
	afx_msg void OnEnquery();
	afx_msg void OnExit();
	afx_msg void OnFirst();
	afx_msg void OnLast();
	afx_msg void OnNew();
	afx_msg void OnNext();
	afx_msg void OnPrior();
	afx_msg void OnSave();
	virtual BOOL OnInitDialog();
		// NOTE: the ClassWizard will add member functions here
	//}}AFX_MSG
	DECLARE_MESSAGE_MAP()
};

//{{AFX_INSERT_LOCATION}}
// Microsoft Visual C++ will insert additional declarations immediately before the previous line.

#endif // !defined(AFX_BOOKDLG_H__A7F5E5B7_F29A_4A7D_9DF6_582B87FC543E__INCLUDED_)


汪曙生
#if !defined(AFX_BORROWDATASET_H__19C367C8_1A07_4EF4_A829_C85594AB65B0__INCLUDED_)
#define AFX_BORROWDATASET_H__19C367C8_1A07_4EF4_A829_C85594AB65B0__INCLUDED_

#if _MSC_VER > 1000
#pragma once
#endif // _MSC_VER > 1000
// BorrowDataSet.h : header file
//

/////////////////////////////////////////////////////////////////////////////
// CBorrowDataSet recordset

class CBorrowDataSet : public CRecordset
{
public:
	CBorrowDataSet(CDatabase* pDatabase = NULL);
	DECLARE_DYNAMIC(CBorrowDataSet)

// Field/Param Data
	//{{AFX_FIELD(CBorrowDataSet, CRecordset)
	long	m_ID;
	CString	m_READER_ID;
	CString	m_BOOK_ID;
	CTime	m_BORROW_DATE;
	CString	m_B_CLERK_ID;
	
	//}}AFX_FIELD


// Overrides
	// ClassWizard generated virtual function overrides
	//{{AFX_VIRTUAL(CBorrowDataSet)
	public:
	virtual CString GetDefaultConnect();    // Default connection string
	virtual CString GetDefaultSQL();    // Default SQL for Recordset
	virtual void DoFieldExchange(CFieldExchange* pFX);  // RFX support
	//}}AFX_VIRTUAL

// Implementation
#ifdef _DEBUG
	virtual void AssertValid() const;
	virtual void Dump(CDumpContext& dc) const;
#endif
};

//{{AFX_INSERT_LOCATION}}
// Microsoft Visual C++ will insert additional declarations immediately before the previous line.

#endif // !defined(AFX_BORROWDATASET_H__19C367C8_1A07_4EF4_A829_C85594AB65B0__INCLUDED_)



王勇 韩凯凯
#if !defined(AFX_BORROWDLG_H__0ADFE907_8B58_4710_BF7D_2F042E1ACF7D__INCLUDED_)
#define AFX_BORROWDLG_H__0ADFE907_8B58_4710_BF7D_2F042E1ACF7D__INCLUDED_

#if _MSC_VER > 1000
#pragma once
#endif // _MSC_VER > 1000
// BorrowDlg.h : header file
//

/////////////////////////////////////////////////////////////////////////////
// CBorrowDlg dialog
#include "BorrowDataSet.h"	
#include "ReaderDataSet.h"	
#include "BookDataSet.h"

class CBorrowDlg : public CDialog
{
// Construction
public:
	CBorrowDlg(CWnd* pParent = NULL);   // standard constructor
	CBookDataSet m_rsBookDataSet;
	CReaderDataSet m_rsReaderDataSet;
	CBorrowDataSet m_rsDataSet;


// Dialog Data
	//{{AFX_DATA(CBorrowDlg)
	enum { IDD = IDD_DIALOG_BORROW };
		CString	m_strBookID;
		CString	m_strReaderID;
		// NOTE: the ClassWizard will add data members here
	//}}AFX_DATA


// Overrides
	// ClassWizard generated virtual function overrides
	//{{AFX_VIRTUAL(CBorrowDlg)
	protected:
	virtual void DoDataExchange(CDataExchange* pDX);    // DDX/DDV support
	//}}AFX_VIRTUAL

// Implementation
protected:

	// Generated message map functions
	//{{AFX_MSG(CBorrowDlg)
	afx_msg void OnConfirm();
	afx_msg void OnCancel();
	virtual BOOL OnInitDialog();
		// NOTE: the ClassWizard will add member functions here
	//}}AFX_MSG
	DECLARE_MESSAGE_MAP()
};
extern CLibraryApp theApp;

//{{AFX_INSERT_LOCATION}}
// Microsoft Visual C++ will insert additional declarations immediately before the previous line.

#endif // !defined(AFX_BORROWDLG_H__0ADFE907_8B58_4710_BF7D_2F042E1ACF7D__INCLUDED_)




12月11号
汪曙生
#if !defined(AFX_BORROWSET_H__633337AD_87BD_4784_A087_5545AA9A4C6C__INCLUDED_)
#define AFX_BORROWSET_H__633337AD_87BD_4784_A087_5545AA9A4C6C__INCLUDED_

#if _MSC_VER > 1000
#pragma once
#endif // _MSC_VER > 1000
// BorrowSet.h : header file
//

/////////////////////////////////////////////////////////////////////////////
// CBorrowSet recordset

class CBorrowSet : public CRecordset
{
public:
	CBorrowSet(CDatabase* pDatabase = NULL);
	DECLARE_DYNAMIC(CBorrowSet)

// Field/Param Data
	//{{AFX_FIELD(CBorrowSet, CRecordset)
	CString	m_READER_ID;
	CString	m_BOOK_ID;
	CTime	m_BORROW_DATE;
	CString	m_B_CLERK_ID;
	long	m_ID;
	CString	m_ReaderName;
	//}}AFX_FIELD


// Overrides
	// ClassWizard generated virtual function overrides
	//{{AFX_VIRTUAL(CBorrowSet)
	public:
	virtual CString GetDefaultConnect();    // Default connection string
	virtual CString GetDefaultSQL();    // Default SQL for Recordset
	virtual void DoFieldExchange(CFieldExchange* pFX);  // RFX support
	//}}AFX_VIRTUAL

// Implementation
#ifdef _DEBUG
	virtual void AssertValid() const;
	virtual void Dump(CDumpContext& dc) const;
#endif
};

//{{AFX_INSERT_LOCATION}}
// Microsoft Visual C++ will insert additional declarations immediately before the previous line.

#endif // !defined(AFX_BORROWSET_H__633337AD_87BD_4784_A087_5545AA9A4C6C__INCLUDED_)


岳超刚 韩凯凯 王勇
#if !defined(AFX_CLERKDATASET_H__5AF5B489_0B80_4DEC_BCA1_BA8BDF3EA3D1__INCLUDED_)
#define AFX_CLERKDATASET_H__5AF5B489_0B80_4DEC_BCA1_BA8BDF3EA3D1__INCLUDED_

#if _MSC_VER > 1000
#pragma once
#endif // _MSC_VER > 1000
// ClerkDataSet.h : header file
//

/////////////////////////////////////////////////////////////////////////////
// CClerkDataSet recordset

class CClerkDataSet : public CRecordset
{
public:
	CClerkDataSet(CDatabase* pDatabase = NULL);
	DECLARE_DYNAMIC(CClerkDataSet)

// Field/Param Data
	//{{AFX_FIELD(CClerkDataSet, CRecordset)
	CString	m_NAME;
	CString	m_PASSWORD;
	//}}AFX_FIELD


// Overrides
	// ClassWizard generated virtual function overrides
	//{{AFX_VIRTUAL(CClerkDataSet)
	public:
	virtual CString GetDefaultConnect();    // Default connection string
	virtual CString GetDefaultSQL();    // Default SQL for Recordset
	virtual void DoFieldExchange(CFieldExchange* pFX);  // RFX support
	//}}AFX_VIRTUAL

// Implementation
#ifdef _DEBUG
	virtual void AssertValid() const;
	virtual void Dump(CDumpContext& dc) const;
#endif
};

//{{AFX_INSERT_LOCATION}}
// Microsoft Visual C++ will insert additional declarations immediately before the previous line.

#endif // !defined(AFX_CLERKDATASET_H__5AF5B489_0B80_4DEC_BCA1_BA8BDF3EA3D1__INCLUDED_)
