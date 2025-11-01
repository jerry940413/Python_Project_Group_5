import random

def create_board(rows, cols, mines):
    # 隨機創造地圖並埋地雷
    return

def count_adjacent_mines(board, r, c):
    # 計算指定格子周圍的地雷數
    return

def check_victory(board, revealed):
    # 判斷是否非地雷的都被翻開
    return True
#以上由羅靖宥負責

def show_board(board, revealed):
    # 顯示棋盤目前狀態
    return

def introduction():
    # 遊戲介紹
    print("歡迎來到《採地雷遊戲》!")
    print("請翻開所有安全的格子，不要踩到地雷\n")
    print("請依序輸入列與行的編號，例如：「1 2」表示第1列第2行。")
    print("顯示符號：")
    print("  □ = 未翻開")
    print("  數字 = 周圍地雷數")
    print("  * = 地雷（遊戲結束）\n")

#以上由謝杰叡負責

def choose_difficulty():
    # 選擇難度
    return

def get_player_input():
    # 取得玩家輸入
    return

def reveal_cell(board, revealed, r, c):
    """翻開格子：踩雷、顯示數字、展開空白"""
    if revealed[r][c]:
        return
    revealed[r][c] = True

    if board[r][c] == "*":
        return  # 踩到雷交給外面判斷

    # 計算周圍地雷
    mines_around = count_adjacent_mines(board, r, c)
    board[r][c] = str(mines_around) if mines_around > 0 else " "

    if mines_around == 0:
        # 自動展開空白格（遞迴）
        return


def game_loop():
    settings = choose_difficulty()
    board = create_board(settings["rows"], settings["cols"], settings["mines"])
    revealed = [[False for _ in range(settings["cols"])]
                for _ in range(settings["rows"])]

    while True:
        show_board(board, revealed)
        row, col = get_player_input()

        # 如果輸入的位置不合理要求重新輸入
        if not (0 <= row < settings["rows"] and 0 <= col < settings["cols"]):
            print("❌ 超出範圍，請重新輸入！")
            continue

        # 翻格子
        reveal_cell(board, revealed, row, col)

        # 判斷勝利與否
        if check_victory(board, revealed):
            show_board(board, revealed)
            break
#以上由黃郁晟負責

def main():
    introduction()
    game_loop()


if __name__ == "__main__":
    main()
