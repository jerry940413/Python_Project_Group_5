  #介紹遊戲規則
  def introduction():
   ```
    print("=" * 30)
    print("歡迎來到《採地雷遊戲》!")
    print("=" * 30)
    print("遊戲目標：翻開所有安全的格子，不要踩到地雷。")
    
    print("\n【操作與顯示說明】")
    # 說明操作模式 (來自夥伴的 play_game 邏輯)
    print("請依序輸入列與行的編號，例如：「1 2」表示第1列第2行。")
    print("  - 輸入 'flag' 切換到插旗模式。")
    print("  - 輸入 'dig' 切換到挖掘模式。")
    print("  - 輸入 'restart' 重新開始新遊戲。")
    
    # 說明顯示符號
    print("\n【顯示符號】")
    print("  □ = 未翻開")
    print("  🚩 = 旗幟")
    print("  數字 = 周圍地雷數 (1~8)")
    print("  💣 = 地雷（遊戲結束）\n")
   ```
#顯示棋盤目前狀態
def show_board(board, revealed):
   ```
    print("\n   " + " ".join([str(i) for i in range(len(board[0]))]))
    print("  " + "--" * len(board[0]))
    for i in range(len(board)):
        row_display = []
        for j in range(len(board[0])):
            if revealed[i][j]:
                row_display.append(board[i][j])
            else:
                row_display.append("□")
        print(f"{i}| " + " ".join(row_display))
    print()
  ```
