# D2.9
from news.models import *

u1 = User.objects.create_user(username = 'Alex')

u2 = User.objects.create_user(username = 'Ann')


Author.objects.create(authorUser = u1)

Author.objects.create(authorUser = u2)


Category.objects.create(name='IT')

Category.objects.create(name='Culture')

Category.objects.create(name='Sport')

Category.objects.create(name='Travel')



a1 = Author.objects.get(id=1)


a2 = Author.objects.get(id=2)


Post.objects.create(author=a1, categoryType='NW', title='UNTOLD AMERICA', text='The Native women reclaiming the US "wild places"')


Post.objects.create(author=a1, categoryType='AR', title='The overlooked masterpiece warning of a Cold War apocalypse', text='The artist Oskar Kokoschka reworked ancient myths to express his fears for humanity. Daisy Dunn explores the meaning of the remarkable Prometheus Triptych – and how it resonates today.')


Post.objects.create(author=a2, categoryType='AR', title='Fifa World Cup Qatar 2022', text='On Sunday, the one-year countdown to the Fifa World Cup Qatar 2022 begins. What can fans expect at the tournament?')


Post.objects.get(id=1).postCategory.add(Category.objects.get(id=2))

Post.objects.get(id=1).postCategory.add(Category.objects.get(id=4))

Post.objects.get(id=2).postCategory.add(Category.objects.get(id=2))

Post.objects.get(id=3).postCategory.add(Category.objects.get(id=3))


Comment.objects.create(commentPost=Post.objects.get(id=1), commentUser=Author.objects.get(id=1).authorUser, text='interesting news')

Comment.objects.create(commentPost=Post.objects.get(id=1), commentUser=Author.objects.get(id=2).authorUser, text='informative')


Comment.objects.create(commentPost=Post.objects.get(id=2), commentUser=Author.objects.get(id=2).authorUser, text='amazing')


Comment.objects.create(commentPost=Post.objects.get(id=3), commentUser=Author.objects.get(id=1).authorUser, text='not interesting')


Comment.objects.get(id=1).like()


Comment.objects.get(id=2).dislike()

Comment.objects.get(id=2).dislike()


Comment.objects.get(id=3).like()

Comment.objects.get(id=3).like()

Comment.objects.get(id=3).like()


Comment.objects.get(id=4).dislike()

Comment.objects.get(id=4).dislike()

Comment.objects.get(id=4).dislike()

Comment.objects.get(id=4).dislike()


Post.objects.get(id=1).dislike()

Post.objects.get(id=1).dislike()

Post.objects.get(id=1).dislike()


Post.objects.get(id=2).like()

Post.objects.get(id=2).like()

Post.objects.get(id=2).like()


Post.objects.get(id=3).dislike()


a1.update_rating()

a2.update_rating()


a = Author.objects.order_by('-ratingAuthor')[:1]
for i in a:
  i.ratingAuthor
  i.authorUser.username


p = Post.objects.order_by('-rating')[:1]
for i in p:
  i.dateCreation
  i.author.authorUser
  i.rating
  i.title
  i.preview()
 

Comment.objects.filter(commentPost=p).values('dateCreation', 'commentUser', 'rating', 'text')
