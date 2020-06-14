Python 3.6.8 (tags/v3.6.8:3c6b436a57, Dec 24 2018, 00:16:47) [MSC v.1916 64 bit (AMD64)] on win32
Type "help", "copyright", "credits" or "license()" for more information.
>>> 
from collections import namedtuple

Chesser = namedtuple('Chesser', 'Name Value Color')
Point = namedtuple('Point', 'X Y')

BlackOne = Chessman('黑子', 1, (45, 45, 45))
WhiteOne= Chessman('白子', 2, (219, 219, 219))

offset = [(1, 0), (0, 1), (1, 1), (1, -1)]


class Checkboard:
    def __init__(self, line_points):
        self._line_points = line_points
        self._checkboard = [[0] * line_points for _ in range(line_points)]

    def _get_checkboard(self):
        return self._checkboard

    checkboard = property(_get_checkboard)

    # 判断是否可落子
    def CanDrop(self, point):
        return self._checkerboard[point.Y][point.X] == 0

    def drop(self, chessman, point):
        """
        落子
        :param chesser:
        :param point:落子位置
        :return:若该子落下之后即可获胜，则返回获胜方，否则返回 None
        """
        print(f'{chesser.Name} ({point.X}, {point.Y})')
        self._checkboard[point.Y][point.X] = chesser.Value

        if self._win(point):
            print(f'{chesser.Name}获胜')
            return chesser

    # 判断是否赢了
    def _win(self, point):
        cur_value = self._checkboard[point.Y][point.X]
        for onestep in offset:
            if self._CountIn(point, cur_value, onestep[0], onestep[1]):
                return True

    def _CountIn(self, point, value, x_offset, y_offset):
        count = 1
        for step in range(1, 5):
            x = point.X + step * x_offset
            y = point.Y + step * y_offset
            if 0 <= x < self._line_points and 0 <= y < self._line_points and self._checkerboard[y][x] == value:
                count += 1
            else:
                break
        for step in range(1, 5):
            x = point.X - step * x_offset
            y = point.Y - step * y_offset
            if 0 <= x < self._line_points and 0 <= y < self._line_points and self._checkerboard[y][x] == value:
                count += 1
            else:
                break

        return count >= 5
