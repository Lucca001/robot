# robotclass ToyRobot:
    def __init__(self):
        self.actions = {
            'move forward': self.move_forward,
            'turn left': self.turn_left,
            'turn right': self.turn_right,
            'greet': self.greet
        }
        self.direction = 'north'
        self.position = (0, 0)

    def move_forward(self):
        x, y = self.position
        if self.direction == 'north':
            self.position = (x, y + 1)
        elif self.direction == 'south':
            self.position = (x, y - 1)
        elif self.direction == 'east':
            self.position = (x + 1, y)
        elif self.direction == 'west':
            self.position = (x - 1, y)

    def turn_left(self):
        if self.direction == 'north':
            self.direction = 'west'
        elif self.direction == 'west':
            self.direction = 'south'
        elif self.direction == 'south':
            self.direction = 'east'
        elif self.direction == 'east':
            self.direction = 'north'

    def turn_right(self):
        if self.direction == 'north':
            self.direction = 'east'
        elif self.direction == 'east':
            self.direction = 'south'
        elif self.direction == 'south':
            self.direction = 'west'
        elif self.direction == 'west':
            self.direction = 'north'

    def greet(self):
        print('Hello, I am your toy robot!')

    def execute_action(self, action_name):
        if action_name in self.actions:
            self.actions[action_name]()
        else:
            print(f'Action {action_name} not recognized.')


if __name__ == '__main__':
    robot = ToyRobot()
    robot.greet()

    user_input = input('Enter an action (move forward, turn left, turn right, greet): ')
    robot.execute_action(user_input)

    user_input = input('Enter another action: ')
    robot.execute_action(user_input)
